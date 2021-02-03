---
title: Confirmar aceitação do cliente do Contrato de Cliente Microsoft
description: Saiba como confirmar a aceitação do Cliente do Microsoft Customer Agreement utilizando APIs do Partner Center.
ms.date: 02/04/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 239ca43c70fb8aa7f0d06e564e6c0726b235ffbe
ms.sourcegitcommit: a25d4951f25502cdf90cfb974022c5e452205f42
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/04/2020
ms.locfileid: "97770075"
---
# <a name="confirm-customer-acceptance-of-the-microsoft-customer-agreement-using-partner-center-apis"></a><span data-ttu-id="a0d45-103">Confirme a aceitação do cliente do Acordo de Cliente da Microsoft utilizando APIs do Partner Center</span><span class="sxs-lookup"><span data-stu-id="a0d45-103">Confirm customer acceptance of the Microsoft Customer Agreement using Partner Center APIs</span></span>

<span data-ttu-id="a0d45-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="a0d45-104">**Applies to:**</span></span>

- <span data-ttu-id="a0d45-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="a0d45-105">Partner Center</span></span>

<span data-ttu-id="a0d45-106">O Partner Center suporta atualmente a confirmação da aceitação pelo cliente do Microsoft Customer Agreement apenas na nuvem pública da *Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="a0d45-106">Partner Center currently supports confirmation of customer acceptance of the Microsoft Customer Agreement only in the *Microsoft public cloud*.</span></span> <span data-ttu-id="a0d45-107">Esta funcionalidade não se aplica atualmente a:</span><span class="sxs-lookup"><span data-stu-id="a0d45-107">This functionality doesn't currently apply to:</span></span>

- <span data-ttu-id="a0d45-108">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="a0d45-108">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="a0d45-109">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="a0d45-109">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="a0d45-110">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="a0d45-110">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="a0d45-111">Este artigo descreve como confirmar ou re-confirmar a aceitação do cliente do Microsoft Customer Agreement.</span><span class="sxs-lookup"><span data-stu-id="a0d45-111">This article describes how to confirm or re-confirm customer acceptance of the Microsoft Customer Agreement.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a0d45-112">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="a0d45-112">Prerequisites</span></span>

- <span data-ttu-id="a0d45-113">Se estiver a utilizar o Partner Center .NET SDK, é necessária a versão 1.14 ou mais recente.</span><span class="sxs-lookup"><span data-stu-id="a0d45-113">If you are using the Partner Center .NET SDK, version 1.14 or newer is required.</span></span>

- <span data-ttu-id="a0d45-114">Credenciais descritas na [autenticação do Partner Center](./partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="a0d45-114">Credentials as described in [Partner Center authentication](./partner-center-authentication.md).</span></span> <span data-ttu-id="a0d45-115">*Este cenário suporta apenas a autenticação App+User.*</span><span class="sxs-lookup"><span data-stu-id="a0d45-115">*This scenario only supports App+User authentication.*</span></span>

- <span data-ttu-id="a0d45-116">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="a0d45-116">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="a0d45-117">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="a0d45-117">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="a0d45-118">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="a0d45-118">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="a0d45-119">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="a0d45-119">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="a0d45-120">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="a0d45-120">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="a0d45-121">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="a0d45-121">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="a0d45-122">A data **(data Acordada)** quando o cliente aceitou o Acordo de Cliente da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a0d45-122">The date (**dateAgreed**) when the customer accepted the Microsoft Customer Agreement.</span></span>

- <span data-ttu-id="a0d45-123">Informação sobre o utilizador da organização do cliente que aceitou o Acordo de Cliente da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a0d45-123">Information about the user from the customer organization that accepted the Microsoft Customer Agreement.</span></span> <span data-ttu-id="a0d45-124">O que está incluído:</span><span class="sxs-lookup"><span data-stu-id="a0d45-124">This includes:</span></span>
  - <span data-ttu-id="a0d45-125">Nome próprio</span><span class="sxs-lookup"><span data-stu-id="a0d45-125">First name</span></span>
  - <span data-ttu-id="a0d45-126">Apelido</span><span class="sxs-lookup"><span data-stu-id="a0d45-126">Last name</span></span>
  - <span data-ttu-id="a0d45-127">Endereço de e-mail</span><span class="sxs-lookup"><span data-stu-id="a0d45-127">Email address</span></span>
  - <span data-ttu-id="a0d45-128">Número de telefone (opcional)</span><span class="sxs-lookup"><span data-stu-id="a0d45-128">Phone number (optional)</span></span>

## <a name="net"></a><span data-ttu-id="a0d45-129">.NET</span><span class="sxs-lookup"><span data-stu-id="a0d45-129">.NET</span></span>

<span data-ttu-id="a0d45-130">Para confirmar ou confirmar a aceitação do cliente do Acordo de Cliente da Microsoft:</span><span class="sxs-lookup"><span data-stu-id="a0d45-130">To confirm or re-confirm customer acceptance of the Microsoft Customer Agreement:</span></span>

1. <span data-ttu-id="a0d45-131">Recupere os metadados do acordo para o Acordo de Cliente da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a0d45-131">Retrieve the agreement metadata for the Microsoft Customer Agreement.</span></span> <span data-ttu-id="a0d45-132">Tem de obter o **modeloId** do Microsoft Customer Agreement.</span><span class="sxs-lookup"><span data-stu-id="a0d45-132">You must obtain the **templateId** of the Microsoft Customer Agreement.</span></span> <span data-ttu-id="a0d45-133">Para mais detalhes, consulte [obter metadados de acordo para o Acordo de Cliente da Microsoft.](get-customer-agreement-metadata.md)</span><span class="sxs-lookup"><span data-stu-id="a0d45-133">For more details, see [Get agreement metadata for Microsoft Customer Agreement](get-customer-agreement-metadata.md).</span></span>

   ```csharp
   // IAggregatePartner partnerOperations;

   string agreementType = "MicrosoftCustomerAgreement";

   var microsoftCustomerAgreementDetails = partnerOperations.AgreementDetails.ByAgreementType(agreementType).Get().Items.Single();
   ```

2. <span data-ttu-id="a0d45-134">Crie um novo objeto **do Acordo** que contenha detalhes da confirmação.</span><span class="sxs-lookup"><span data-stu-id="a0d45-134">Create a new **Agreement** object containing details of the confirmation.</span></span>

3. <span data-ttu-id="a0d45-135">Utilize a coleção **IAgreggatePartner.Customers** e ligue para o método **ById** com o id específico **cliente-inquilino.**</span><span class="sxs-lookup"><span data-stu-id="a0d45-135">Use the **IAgreggatePartner.Customers** collection and call the **ById** method with the specified **customer-tenant-id**.</span></span>

4. <span data-ttu-id="a0d45-136">Utilize a propriedade **Agreements,** seguida de chamar **Create** or **CreateAsync**.</span><span class="sxs-lookup"><span data-stu-id="a0d45-136">Use the **Agreements** property, followed by calling **Create** or **CreateAsync**.</span></span>

   ```csharp
   // string selectedCustomerId;

   var agreementToCreate = new Agreement
   {
       DateAgreed = DateTime.UtcNow,
       TemplateId = microsoftCustomerAgreementDetails.TemplateId,
       PrimaryContact = new Contact
       {
           FirstName = "Tania",
           LastName = "Carr",
           Email = "someone@example.com",
           PhoneNumber = "1234567890"
       }
   };

   Agreement agreement = partnerOperations.Customers.ById(selectedCustomerId).Agreements.Create(agreementToCreate);
   ```

<span data-ttu-id="a0d45-137">Uma amostra completa pode ser encontrada na classe [CreateCustomerAgreement](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/CreateCustomerAgreement.cs) do projeto de [aplicações de teste](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples) de consola.</span><span class="sxs-lookup"><span data-stu-id="a0d45-137">A complete sample can be found in the [CreateCustomerAgreement](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/CreateCustomerAgreement.cs) class from the [console test app](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples) project.</span></span>

## <a name="rest-request"></a><span data-ttu-id="a0d45-138">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="a0d45-138">REST request</span></span>

<span data-ttu-id="a0d45-139">Para confirmar ou confirmar a aceitação do cliente do Acordo de Cliente da Microsoft:</span><span class="sxs-lookup"><span data-stu-id="a0d45-139">To confirm or re-confirm customer acceptance of the Microsoft Customer Agreement:</span></span>

1. <span data-ttu-id="a0d45-140">Recupere os metadados do acordo para o Acordo de Cliente da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a0d45-140">Retrieve the agreement metadata for the Microsoft Customer Agreement.</span></span> <span data-ttu-id="a0d45-141">Tem de obter o **modeloId** do Microsoft Customer Agreement.</span><span class="sxs-lookup"><span data-stu-id="a0d45-141">You must obtain the **templateId** of the Microsoft Customer Agreement.</span></span> <span data-ttu-id="a0d45-142">Para mais detalhes, consulte [obter metadados de acordo para o Acordo de Cliente da Microsoft.](get-customer-agreement-metadata.md)</span><span class="sxs-lookup"><span data-stu-id="a0d45-142">For more details, see [Get agreement metadata for Microsoft Customer Agreement](get-customer-agreement-metadata.md).</span></span>

2. <span data-ttu-id="a0d45-143">Crie um novo recurso [ **do Agreement**](agreement-resources.md) para confirmar que um cliente aceitou o Acordo de Cliente da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a0d45-143">Create a new [**Agreement** resource](agreement-resources.md) to confirm that a customer has accepted the Microsoft Customer Agreement.</span></span> <span data-ttu-id="a0d45-144">Utilize a seguinte [sintaxe de pedido DEE](#request-syntax).</span><span class="sxs-lookup"><span data-stu-id="a0d45-144">Use the following [REST request syntax](#request-syntax).</span></span>

### <a name="request-syntax"></a><span data-ttu-id="a0d45-145">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="a0d45-145">Request syntax</span></span>

| <span data-ttu-id="a0d45-146">Método</span><span class="sxs-lookup"><span data-stu-id="a0d45-146">Method</span></span> | <span data-ttu-id="a0d45-147">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="a0d45-147">Request URI</span></span>                                                                                        |
|--------|----------------------------------------------------------------------------------------------------|
| <span data-ttu-id="a0d45-148">POST</span><span class="sxs-lookup"><span data-stu-id="a0d45-148">POST</span></span>   | <span data-ttu-id="a0d45-149">[*\{ baseURL \}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/acordos HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="a0d45-149">[*\{baseURL\}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/agreements HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="a0d45-150">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="a0d45-150">URI parameter</span></span>

<span data-ttu-id="a0d45-151">Utilize o seguinte parâmetro de consulta para especificar o cliente que está a confirmar.</span><span class="sxs-lookup"><span data-stu-id="a0d45-151">Use the following query parameter to specify the customer that you're confirming.</span></span>

| <span data-ttu-id="a0d45-152">Nome</span><span class="sxs-lookup"><span data-stu-id="a0d45-152">Name</span></span>               | <span data-ttu-id="a0d45-153">Tipo</span><span class="sxs-lookup"><span data-stu-id="a0d45-153">Type</span></span> | <span data-ttu-id="a0d45-154">Necessário</span><span class="sxs-lookup"><span data-stu-id="a0d45-154">Required</span></span> | <span data-ttu-id="a0d45-155">Descrição</span><span class="sxs-lookup"><span data-stu-id="a0d45-155">Description</span></span>                                                                                 |
|--------------------|------|----------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="a0d45-156">cliente-inquilino-id</span><span class="sxs-lookup"><span data-stu-id="a0d45-156">customer-tenant-id</span></span> | <span data-ttu-id="a0d45-157">GUID</span><span class="sxs-lookup"><span data-stu-id="a0d45-157">GUID</span></span> | <span data-ttu-id="a0d45-158">Sim</span><span class="sxs-lookup"><span data-stu-id="a0d45-158">Yes</span></span> | <span data-ttu-id="a0d45-159">O valor é um **cliente-id-inquilino-inquilino-id,** que é um identificador que lhe permite especificar um cliente.</span><span class="sxs-lookup"><span data-stu-id="a0d45-159">The value is a GUID-formatted **customer-tenant-id**, which is an identifier that allows you to specify a customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="a0d45-160">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="a0d45-160">Request headers</span></span>

<span data-ttu-id="a0d45-161">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="a0d45-161">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="a0d45-162">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="a0d45-162">Request body</span></span>

<span data-ttu-id="a0d45-163">Esta tabela descreve as propriedades necessárias no corpo de pedido REST.</span><span class="sxs-lookup"><span data-stu-id="a0d45-163">This table describes the required properties in the REST request body.</span></span>

| <span data-ttu-id="a0d45-164">Nome</span><span class="sxs-lookup"><span data-stu-id="a0d45-164">Name</span></span>      | <span data-ttu-id="a0d45-165">Tipo</span><span class="sxs-lookup"><span data-stu-id="a0d45-165">Type</span></span>   | <span data-ttu-id="a0d45-166">Descrição</span><span class="sxs-lookup"><span data-stu-id="a0d45-166">Description</span></span>                                                                                  |
|-----------|--------|----------------------------------------------------------------------------------------------|
| <span data-ttu-id="a0d45-167">Contrato</span><span class="sxs-lookup"><span data-stu-id="a0d45-167">Agreement</span></span> | <span data-ttu-id="a0d45-168">objeto</span><span class="sxs-lookup"><span data-stu-id="a0d45-168">object</span></span> | <span data-ttu-id="a0d45-169">Detalhes fornecidos pelo parceiro para confirmar a aceitação do cliente do Acordo de Cliente da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a0d45-169">Details provided by partner to confirm customer acceptance of the Microsoft Customer Agreement.</span></span> |

#### <a name="agreement"></a><span data-ttu-id="a0d45-170">Contrato</span><span class="sxs-lookup"><span data-stu-id="a0d45-170">Agreement</span></span>

<span data-ttu-id="a0d45-171">Esta tabela descreve os campos mínimos necessários para criar um recurso [ **do Acordo.**](agreement-resources.md)</span><span class="sxs-lookup"><span data-stu-id="a0d45-171">This table describes the minimum required fields to create an [**Agreement** resource](agreement-resources.md).</span></span>

| <span data-ttu-id="a0d45-172">Propriedade</span><span class="sxs-lookup"><span data-stu-id="a0d45-172">Property</span></span>       | <span data-ttu-id="a0d45-173">Tipo</span><span class="sxs-lookup"><span data-stu-id="a0d45-173">Type</span></span>   | <span data-ttu-id="a0d45-174">Descrição</span><span class="sxs-lookup"><span data-stu-id="a0d45-174">Description</span></span>                              |
|----------------|--------|------------------------------------------|
| <span data-ttu-id="a0d45-175">principalContact</span><span class="sxs-lookup"><span data-stu-id="a0d45-175">primaryContact</span></span> | [<span data-ttu-id="a0d45-176">Contacto</span><span class="sxs-lookup"><span data-stu-id="a0d45-176">Contact</span></span>](./utility-resources.md#contact) | <span data-ttu-id="a0d45-177">Informações sobre o utilizador da organização do cliente que aceitou o Acordo de Cliente da Microsoft, incluindo:  **primeiro Nome,** **último Nome,** **e-mail** e **telefoneNumber** (opcional)</span><span class="sxs-lookup"><span data-stu-id="a0d45-177">Information about the user from the customer organization who accepted the Microsoft Customer Agreement, including:  **firstName**, **lastName**, **email** and **phoneNumber** (optional)</span></span> |
| <span data-ttu-id="a0d45-178">dataA acordado</span><span class="sxs-lookup"><span data-stu-id="a0d45-178">dateAgreed</span></span>     | <span data-ttu-id="a0d45-179">cadeia no formato de hora de data UTC</span><span class="sxs-lookup"><span data-stu-id="a0d45-179">string in UTC date time format</span></span> |<span data-ttu-id="a0d45-180">A data em que o cliente aceitou o contrato.</span><span class="sxs-lookup"><span data-stu-id="a0d45-180">The date when the customer accepted the agreement.</span></span> |
| <span data-ttu-id="a0d45-181">templateId</span><span class="sxs-lookup"><span data-stu-id="a0d45-181">templateId</span></span>     | <span data-ttu-id="a0d45-182">string</span><span class="sxs-lookup"><span data-stu-id="a0d45-182">string</span></span> | <span data-ttu-id="a0d45-183">Identificador único do tipo de contrato aceite pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="a0d45-183">Unique identifier of the agreement type accepted by the customer.</span></span> <span data-ttu-id="a0d45-184">Pode obter o **modeloId** para o Acordo de Cliente da Microsoft recuperando os metadados do acordo para o Microsoft Customer Agreement.</span><span class="sxs-lookup"><span data-stu-id="a0d45-184">You can obtain the **templateId** for Microsoft Customer Agreement by retrieving the agreement metadata for Microsoft Customer Agreement.</span></span> <span data-ttu-id="a0d45-185">Consulte [os metadados de acordo para o Microsoft Customer Agreement](./get-customer-agreement-metadata.md) para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="a0d45-185">See [Get agreement metadata for Microsoft Customer Agreement](./get-customer-agreement-metadata.md) for details.</span></span> |
| <span data-ttu-id="a0d45-186">tipo</span><span class="sxs-lookup"><span data-stu-id="a0d45-186">type</span></span>           | <span data-ttu-id="a0d45-187">string</span><span class="sxs-lookup"><span data-stu-id="a0d45-187">string</span></span> | <span data-ttu-id="a0d45-188">Tipo de acordo aceite pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="a0d45-188">Agreement type accepted by the customer.</span></span> <span data-ttu-id="a0d45-189">Utilize "MicrosoftCustomerAgreement" se o cliente aceitar o Acordo de Cliente da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a0d45-189">Use "MicrosoftCustomerAgreement" if customer accepted the Microsoft Customer Agreement.</span></span> |

#### <a name="request-example"></a><span data-ttu-id="a0d45-190">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="a0d45-190">Request example</span></span>

```http
POST https://api.partnercenter.microsoft.com/v1/customers/14876998-c0dc-46e6-9d0c-65a57a6c32ec/agreements HTTP/1.1
Authorization: Bearer <token>
Content-Type: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
{
    "primaryContact": {
        "firstName": "Tania",
        "lastName": "Carr",
        "email": "someone@example.com",
        "phoneNumber": "1234567890"
    },
    "templateId": "117a77b0-9360-443b-8795-c6dedc750cf9",
    "dateAgreed": "2018-06-14T00:00:00.000Z",
    "type": "MicrosoftCustomerAgreement"
}
```

## <a name="rest-response"></a><span data-ttu-id="a0d45-191">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="a0d45-191">REST response</span></span>

<span data-ttu-id="a0d45-192">Se for bem sucedido, este método devolve um recurso [ **do Acordo**](./agreement-resources.md).</span><span class="sxs-lookup"><span data-stu-id="a0d45-192">If successful, this method returns an [**Agreement** resource](./agreement-resources.md).</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="a0d45-193">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="a0d45-193">Response success and error codes</span></span>

<span data-ttu-id="a0d45-194">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="a0d45-194">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span>

<span data-ttu-id="a0d45-195">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="a0d45-195">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="a0d45-196">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="a0d45-196">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

#### <a name="response-example"></a><span data-ttu-id="a0d45-197">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="a0d45-197">Response example</span></span>

```http
HTTP/1.1 201 Created
Content-Length: 261
Content-Type: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
{
    "userId": "3d6f2c09-eb40-48ca-a4b3-d24c9c007531",
    "primaryContact": {
        "firstName": "Tania",
        "lastName": "Carr",
        "email": "someone@example.com",
        "phoneNumber": "1234567890"
    },
    "templateId": "117a77b0-9360-443b-8795-c6dedc750cf9",
    "dateAgreed": "2018-06-14T00:00:00.000Z",
    "type": "MicrosoftCustomerAgreement"
}
```
