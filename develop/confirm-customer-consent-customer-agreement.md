---
title: Confirmar aceitação do cliente do Contrato de Cliente Microsoft
description: Saiba como confirmar a aceitação do Cliente do Microsoft Customer Agreement utilizando APIs do Partner Center.
ms.date: 02/08/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 002508109191ede53cd06f25efc38286647fd67c
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/10/2021
ms.locfileid: "111974017"
---
# <a name="confirm-customer-acceptance-of-the-microsoft-customer-agreement-using-partner-center-apis"></a><span data-ttu-id="02fa4-103">Confirme a aceitação do cliente do Acordo de Cliente da Microsoft utilizando APIs do Partner Center</span><span class="sxs-lookup"><span data-stu-id="02fa4-103">Confirm customer acceptance of the Microsoft Customer Agreement using Partner Center APIs</span></span>

<span data-ttu-id="02fa4-104">**Aplica-se a**: Centro de Parceiros</span><span class="sxs-lookup"><span data-stu-id="02fa4-104">**Applies to**: Partner Center</span></span>

<span data-ttu-id="02fa4-105">**Não se aplica a:** Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="02fa4-105">**Does not apply to**: Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="02fa4-106">O Partner Center suporta atualmente a confirmação da aceitação pelo cliente do Microsoft Customer Agreement apenas na nuvem pública da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="02fa4-106">Partner Center currently supports confirmation of customer acceptance of the Microsoft Customer Agreement only in the Microsoft public cloud.</span></span>

<span data-ttu-id="02fa4-107">Este artigo descreve como confirmar ou reconfirmar a aceitação do cliente do Microsoft Customer Agreement.</span><span class="sxs-lookup"><span data-stu-id="02fa4-107">This article describes how to confirm or reconfirm customer acceptance of the Microsoft Customer Agreement.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="02fa4-108">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="02fa4-108">Prerequisites</span></span>

- <span data-ttu-id="02fa4-109">Se estiver a utilizar o Partner Center .NET SDK, é necessária a versão 1.14 ou mais recente.</span><span class="sxs-lookup"><span data-stu-id="02fa4-109">If you are using the Partner Center .NET SDK, version 1.14 or newer is required.</span></span>

- <span data-ttu-id="02fa4-110">Credenciais descritas na [autenticação do Partner Center](./partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="02fa4-110">Credentials as described in [Partner Center authentication](./partner-center-authentication.md).</span></span> <span data-ttu-id="02fa4-111">*Este cenário suporta apenas a autenticação App+User.*</span><span class="sxs-lookup"><span data-stu-id="02fa4-111">*This scenario only supports App+User authentication.*</span></span>

- <span data-ttu-id="02fa4-112">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="02fa4-112">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="02fa4-113">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="02fa4-113">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="02fa4-114">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="02fa4-114">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="02fa4-115">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="02fa4-115">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="02fa4-116">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="02fa4-116">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="02fa4-117">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="02fa4-117">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="02fa4-118">A data **(data Acordada)** quando o cliente aceitou o Acordo de Cliente da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="02fa4-118">The date (**dateAgreed**) when the customer accepted the Microsoft Customer Agreement.</span></span>

- <span data-ttu-id="02fa4-119">Informação sobre o utilizador da organização do cliente que aceitou o Acordo de Cliente da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="02fa4-119">Information about the user from the customer organization that accepted the Microsoft Customer Agreement.</span></span> <span data-ttu-id="02fa4-120">O que está incluído:</span><span class="sxs-lookup"><span data-stu-id="02fa4-120">This includes:</span></span>
  - <span data-ttu-id="02fa4-121">Nome próprio</span><span class="sxs-lookup"><span data-stu-id="02fa4-121">First name</span></span>
  - <span data-ttu-id="02fa4-122">Apelido</span><span class="sxs-lookup"><span data-stu-id="02fa4-122">Last name</span></span>
  - <span data-ttu-id="02fa4-123">Endereço de e-mail</span><span class="sxs-lookup"><span data-stu-id="02fa4-123">Email address</span></span>
  - <span data-ttu-id="02fa4-124">Telefone número (opcional)</span><span class="sxs-lookup"><span data-stu-id="02fa4-124">Phone number (optional)</span></span>
- <span data-ttu-id="02fa4-125">Se os valores seguintes mudarem para um cliente, o Partner Center permitirá a criação de outro acordo para esse cliente: Endereço de e-mail de nome de primeiro nome Telefone número Caso os parceiros receberão o seguinte código de erro, devido à criação de um cliente duplicado</span><span class="sxs-lookup"><span data-stu-id="02fa4-125">If the following values change for a customer, Partner Center  will allow for another agreement to be created for that customer:       First Name       Last Name       Email address       Phone number Otherwise partners will receive the following error code, due to a duplicate customer being created</span></span>


```
{
"code": 600061,
"message": "A partner confirmed agreement already exists for the customer.",
"description": "A partner confirmed agreement already exists for the customer.",
"errorName": "PartnerConfirmedAgreementAlreadyExists",
"isRetryable": false,
"parameters": {},
"errorMessageExtended": "InternalErrorCode=600061"
}
 ```

## <a name="net"></a><span data-ttu-id="02fa4-126">.NET</span><span class="sxs-lookup"><span data-stu-id="02fa4-126">.NET</span></span>

<span data-ttu-id="02fa4-127">Para confirmar ou reconfirmar a aceitação do cliente do Acordo de Cliente da Microsoft:</span><span class="sxs-lookup"><span data-stu-id="02fa4-127">To confirm or reconfirm customer acceptance of the Microsoft Customer Agreement:</span></span>

1. <span data-ttu-id="02fa4-128">Recupere os metadados do acordo para o Acordo de Cliente da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="02fa4-128">Retrieve the agreement metadata for the Microsoft Customer Agreement.</span></span> <span data-ttu-id="02fa4-129">Tem de obter o **modeloId** do Microsoft Customer Agreement.</span><span class="sxs-lookup"><span data-stu-id="02fa4-129">You must obtain the **templateId** of the Microsoft Customer Agreement.</span></span> <span data-ttu-id="02fa4-130">Para obter mais informações, consulte [obter metadados de acordo para o Acordo de Cliente da Microsoft.](get-customer-agreement-metadata.md)</span><span class="sxs-lookup"><span data-stu-id="02fa4-130">For more information, see [Get agreement metadata for Microsoft Customer Agreement](get-customer-agreement-metadata.md).</span></span>

   ```csharp
   // IAggregatePartner partnerOperations;

   string agreementType = "MicrosoftCustomerAgreement";

   var microsoftCustomerAgreementDetails = partnerOperations.AgreementDetails.ByAgreementType(agreementType).Get().Items.Single();
   ```

2. <span data-ttu-id="02fa4-131">Crie um novo objeto **do Acordo** que contenha detalhes da confirmação.</span><span class="sxs-lookup"><span data-stu-id="02fa4-131">Create a new **Agreement** object containing details of the confirmation.</span></span>

3. <span data-ttu-id="02fa4-132">Utilize a coleção **IAgreggatePartner.Customers** e ligue para o método **ById** com o id específico **cliente-inquilino.**</span><span class="sxs-lookup"><span data-stu-id="02fa4-132">Use the **IAgreggatePartner.Customers** collection and call the **ById** method with the specified **customer-tenant-id**.</span></span>

4. <span data-ttu-id="02fa4-133">Utilize a propriedade **Agreements,** seguida de chamar **Create** or **CreateAsync**.</span><span class="sxs-lookup"><span data-stu-id="02fa4-133">Use the **Agreements** property, followed by calling **Create** or **CreateAsync**.</span></span>

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

<span data-ttu-id="02fa4-134">Uma amostra completa pode ser encontrada na classe [CreateCustomerAgreement](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/CreateCustomerAgreement.cs) do projeto de [aplicações de teste](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples) de consola.</span><span class="sxs-lookup"><span data-stu-id="02fa4-134">A complete sample can be found in the [CreateCustomerAgreement](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/CreateCustomerAgreement.cs) class from the [console test app](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples) project.</span></span>

## <a name="rest-request"></a><span data-ttu-id="02fa4-135">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="02fa4-135">REST request</span></span>

<span data-ttu-id="02fa4-136">Para confirmar ou reconfirmar a aceitação do cliente do Acordo de Cliente da Microsoft:</span><span class="sxs-lookup"><span data-stu-id="02fa4-136">To confirm or reconfirm customer acceptance of the Microsoft Customer Agreement:</span></span>

1. <span data-ttu-id="02fa4-137">Recupere os metadados do acordo para o Acordo de Cliente da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="02fa4-137">Retrieve the agreement metadata for the Microsoft Customer Agreement.</span></span> <span data-ttu-id="02fa4-138">Tem de obter o **modeloId** do Microsoft Customer Agreement.</span><span class="sxs-lookup"><span data-stu-id="02fa4-138">You must obtain the **templateId** of the Microsoft Customer Agreement.</span></span> <span data-ttu-id="02fa4-139">Para obter mais informações, consulte [obter metadados de acordo para o Acordo de Cliente da Microsoft.](get-customer-agreement-metadata.md)</span><span class="sxs-lookup"><span data-stu-id="02fa4-139">For more information, see [Get agreement metadata for Microsoft Customer Agreement](get-customer-agreement-metadata.md).</span></span>

2. <span data-ttu-id="02fa4-140">Crie um novo recurso [ **do Agreement**](agreement-resources.md) para confirmar que um cliente aceitou o Acordo de Cliente da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="02fa4-140">Create a new [**Agreement** resource](agreement-resources.md) to confirm that a customer has accepted the Microsoft Customer Agreement.</span></span> <span data-ttu-id="02fa4-141">Utilize a seguinte [sintaxe de pedido DEE](#request-syntax).</span><span class="sxs-lookup"><span data-stu-id="02fa4-141">Use the following [REST request syntax](#request-syntax).</span></span>

### <a name="request-syntax"></a><span data-ttu-id="02fa4-142">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="02fa4-142">Request syntax</span></span>

| <span data-ttu-id="02fa4-143">Método</span><span class="sxs-lookup"><span data-stu-id="02fa4-143">Method</span></span> | <span data-ttu-id="02fa4-144">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="02fa4-144">Request URI</span></span>                                                                                        |
|--------|----------------------------------------------------------------------------------------------------|
| <span data-ttu-id="02fa4-145">POST</span><span class="sxs-lookup"><span data-stu-id="02fa4-145">POST</span></span>   | <span data-ttu-id="02fa4-146">[*\{ baseURL \}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/acordos HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="02fa4-146">[*\{baseURL\}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/agreements HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="02fa4-147">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="02fa4-147">URI parameter</span></span>

<span data-ttu-id="02fa4-148">Utilize o seguinte parâmetro de consulta para especificar o cliente que está a confirmar.</span><span class="sxs-lookup"><span data-stu-id="02fa4-148">Use the following query parameter to specify the customer that you're confirming.</span></span>

| <span data-ttu-id="02fa4-149">Nome</span><span class="sxs-lookup"><span data-stu-id="02fa4-149">Name</span></span>               | <span data-ttu-id="02fa4-150">Tipo</span><span class="sxs-lookup"><span data-stu-id="02fa4-150">Type</span></span> | <span data-ttu-id="02fa4-151">Necessário</span><span class="sxs-lookup"><span data-stu-id="02fa4-151">Required</span></span> | <span data-ttu-id="02fa4-152">Descrição</span><span class="sxs-lookup"><span data-stu-id="02fa4-152">Description</span></span>                                                                                 |
|--------------------|------|----------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="02fa4-153">cliente-inquilino-id</span><span class="sxs-lookup"><span data-stu-id="02fa4-153">customer-tenant-id</span></span> | <span data-ttu-id="02fa4-154">GUID</span><span class="sxs-lookup"><span data-stu-id="02fa4-154">GUID</span></span> | <span data-ttu-id="02fa4-155">Yes</span><span class="sxs-lookup"><span data-stu-id="02fa4-155">Yes</span></span> | <span data-ttu-id="02fa4-156">O valor é um **cliente-id-inquilino-inquilino-id,** que é um identificador que lhe permite especificar um cliente.</span><span class="sxs-lookup"><span data-stu-id="02fa4-156">The value is a GUID-formatted **customer-tenant-id**, which is an identifier that allows you to specify a customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="02fa4-157">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="02fa4-157">Request headers</span></span>

<span data-ttu-id="02fa4-158">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="02fa4-158">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="02fa4-159">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="02fa4-159">Request body</span></span>

<span data-ttu-id="02fa4-160">Esta tabela descreve as propriedades necessárias no corpo de pedido REST.</span><span class="sxs-lookup"><span data-stu-id="02fa4-160">This table describes the required properties in the REST request body.</span></span>

| <span data-ttu-id="02fa4-161">Nome</span><span class="sxs-lookup"><span data-stu-id="02fa4-161">Name</span></span>      | <span data-ttu-id="02fa4-162">Tipo</span><span class="sxs-lookup"><span data-stu-id="02fa4-162">Type</span></span>   | <span data-ttu-id="02fa4-163">Description</span><span class="sxs-lookup"><span data-stu-id="02fa4-163">Description</span></span>                                                                                  |
|-----------|--------|----------------------------------------------------------------------------------------------|
| <span data-ttu-id="02fa4-164">Contrato</span><span class="sxs-lookup"><span data-stu-id="02fa4-164">Agreement</span></span> | <span data-ttu-id="02fa4-165">objeto</span><span class="sxs-lookup"><span data-stu-id="02fa4-165">object</span></span> | <span data-ttu-id="02fa4-166">Detalhes fornecidos pelo parceiro para confirmar a aceitação do cliente do Acordo de Cliente da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="02fa4-166">Details provided by partner to confirm customer acceptance of the Microsoft Customer Agreement.</span></span> |

#### <a name="agreement"></a><span data-ttu-id="02fa4-167">Contrato</span><span class="sxs-lookup"><span data-stu-id="02fa4-167">Agreement</span></span>

<span data-ttu-id="02fa4-168">Esta tabela descreve os campos mínimos necessários para criar um recurso [ **do Acordo.**](agreement-resources.md)</span><span class="sxs-lookup"><span data-stu-id="02fa4-168">This table describes the minimum required fields to create an [**Agreement** resource](agreement-resources.md).</span></span>

| <span data-ttu-id="02fa4-169">Propriedade</span><span class="sxs-lookup"><span data-stu-id="02fa4-169">Property</span></span>       | <span data-ttu-id="02fa4-170">Tipo</span><span class="sxs-lookup"><span data-stu-id="02fa4-170">Type</span></span>   | <span data-ttu-id="02fa4-171">Description</span><span class="sxs-lookup"><span data-stu-id="02fa4-171">Description</span></span>                              |
|----------------|--------|------------------------------------------|
| <span data-ttu-id="02fa4-172">principalContact</span><span class="sxs-lookup"><span data-stu-id="02fa4-172">primaryContact</span></span> | [<span data-ttu-id="02fa4-173">Contacto</span><span class="sxs-lookup"><span data-stu-id="02fa4-173">Contact</span></span>](./utility-resources.md#contact) | <span data-ttu-id="02fa4-174">Informações sobre o utilizador da organização do cliente que aceitou o Acordo de Cliente da Microsoft, incluindo:  **primeiro Nome,** **último Nome,** **e-mail** e **telefoneNumber** (opcional)</span><span class="sxs-lookup"><span data-stu-id="02fa4-174">Information about the user from the customer organization who accepted the Microsoft Customer Agreement, including:  **firstName**, **lastName**, **email**, and **phoneNumber** (optional)</span></span> |
| <span data-ttu-id="02fa4-175">dataA acordado</span><span class="sxs-lookup"><span data-stu-id="02fa4-175">dateAgreed</span></span>     | <span data-ttu-id="02fa4-176">cadeia no formato de hora de data UTC</span><span class="sxs-lookup"><span data-stu-id="02fa4-176">string in UTC date time format</span></span> |<span data-ttu-id="02fa4-177">A data em que o cliente aceitou o contrato.</span><span class="sxs-lookup"><span data-stu-id="02fa4-177">The date when the customer accepted the agreement.</span></span> |
| <span data-ttu-id="02fa4-178">templateId</span><span class="sxs-lookup"><span data-stu-id="02fa4-178">templateId</span></span>     | <span data-ttu-id="02fa4-179">string</span><span class="sxs-lookup"><span data-stu-id="02fa4-179">string</span></span> | <span data-ttu-id="02fa4-180">Identificador único do tipo de contrato aceite pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="02fa4-180">Unique identifier of the agreement type accepted by the customer.</span></span> <span data-ttu-id="02fa4-181">Pode obter o **modeloId** para o Acordo de Cliente da Microsoft recuperando os metadados do acordo para o Microsoft Customer Agreement.</span><span class="sxs-lookup"><span data-stu-id="02fa4-181">You can obtain the **templateId** for Microsoft Customer Agreement by retrieving the agreement metadata for Microsoft Customer Agreement.</span></span> <span data-ttu-id="02fa4-182">Consulte [os metadados de acordo para o Microsoft Customer Agreement](./get-customer-agreement-metadata.md) para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="02fa4-182">See [Get agreement metadata for Microsoft Customer Agreement](./get-customer-agreement-metadata.md) for details.</span></span> |
| <span data-ttu-id="02fa4-183">tipo</span><span class="sxs-lookup"><span data-stu-id="02fa4-183">type</span></span>           | <span data-ttu-id="02fa4-184">string</span><span class="sxs-lookup"><span data-stu-id="02fa4-184">string</span></span> | <span data-ttu-id="02fa4-185">Tipo de acordo aceite pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="02fa4-185">Agreement type accepted by the customer.</span></span> <span data-ttu-id="02fa4-186">Utilize "MicrosoftCustomerAgreement" se o cliente aceitar o Acordo de Cliente da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="02fa4-186">Use "MicrosoftCustomerAgreement" if customer accepted the Microsoft Customer Agreement.</span></span> |

#### <a name="request-example"></a><span data-ttu-id="02fa4-187">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="02fa4-187">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="02fa4-188">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="02fa4-188">REST response</span></span>

<span data-ttu-id="02fa4-189">Se for bem sucedido, este método devolve um recurso [ **do Acordo**](./agreement-resources.md).</span><span class="sxs-lookup"><span data-stu-id="02fa4-189">If successful, this method returns an [**Agreement** resource](./agreement-resources.md).</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="02fa4-190">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="02fa4-190">Response success and error codes</span></span>

<span data-ttu-id="02fa4-191">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="02fa4-191">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span>

<span data-ttu-id="02fa4-192">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="02fa4-192">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="02fa4-193">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="02fa4-193">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

#### <a name="response-example"></a><span data-ttu-id="02fa4-194">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="02fa4-194">Response example</span></span>

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
