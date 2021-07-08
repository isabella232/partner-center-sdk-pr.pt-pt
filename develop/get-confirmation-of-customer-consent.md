---
title: Obter confirmação da aceitação do cliente do Contrato da Microsoft Cloud
description: Este artigo explica como obter a confirmação da aceitação pelo cliente do Microsoft Cloud Agreement.
ms.date: 02/12/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
aauthor: khakiali
ms.author: alikhaki
ms.openlocfilehash: 1b1a8cbacb667e579bcd218a29c3f553afce26c2
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/06/2021
ms.locfileid: "111549268"
---
# <a name="get-confirmation-of-customer-acceptance-of-microsoft-cloud-agreement"></a><span data-ttu-id="0d01a-103">Obter confirmação da aceitação do cliente do Contrato da Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="0d01a-103">Get confirmation of customer acceptance of Microsoft Cloud Agreement</span></span>

<span data-ttu-id="0d01a-104">**Aplica-se a**: Centro de Parceiros</span><span class="sxs-lookup"><span data-stu-id="0d01a-104">**Applies to**: Partner Center</span></span>

<span data-ttu-id="0d01a-105">**Não se aplica a:** Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="0d01a-105">**Does not apply to**: Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="0d01a-106">O recurso **Do Acordo** é atualmente suportado pelo Partner Center apenas na nuvem pública da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="0d01a-106">The **Agreement** resource is currently supported by Partner Center only in the Microsoft public cloud.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0d01a-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="0d01a-107">Prerequisites</span></span>

- <span data-ttu-id="0d01a-108">Se estiver a utilizar o Partner Center .NET SDK, é necessária a versão 1.9 ou a mais recente.</span><span class="sxs-lookup"><span data-stu-id="0d01a-108">If you are using the Partner Center .NET SDK, version 1.9 or newer is required.</span></span>

- <span data-ttu-id="0d01a-109">Se estiver a utilizar o Partner Center Java SDK, é necessária a versão 1.8 ou mais recente.</span><span class="sxs-lookup"><span data-stu-id="0d01a-109">If you are using the Partner Center Java SDK, version 1.8 or newer is required.</span></span>

- <span data-ttu-id="0d01a-110">Credenciais descritas na [autenticação do Partner Center](./partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="0d01a-110">Credentials as described in [Partner Center authentication](./partner-center-authentication.md).</span></span> <span data-ttu-id="0d01a-111">Este cenário apenas suporta app + autenticação do utilizador.</span><span class="sxs-lookup"><span data-stu-id="0d01a-111">This scenario only supports app + user authentication.</span></span>

- <span data-ttu-id="0d01a-112">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="0d01a-112">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="0d01a-113">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="0d01a-113">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="0d01a-114">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="0d01a-114">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="0d01a-115">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="0d01a-115">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="0d01a-116">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="0d01a-116">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="0d01a-117">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="0d01a-117">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="net-version-14-or-newer"></a><span data-ttu-id="0d01a-118">.NET (versão 1.4 ou mais recente)</span><span class="sxs-lookup"><span data-stu-id="0d01a-118">.NET (version 1.4 or newer)</span></span>

<span data-ttu-id="0d01a-119">Para obter confirmação(s) de aceitação do cliente que foi previamente fornecida:</span><span class="sxs-lookup"><span data-stu-id="0d01a-119">To retrieve confirmation(s) of customer acceptance that was previously provided:</span></span>

- <span data-ttu-id="0d01a-120">Utilize a recolha **IAggregatePartner.Customers** e ligue para o método **ById** com o identificador de clientes especificado.</span><span class="sxs-lookup"><span data-stu-id="0d01a-120">Use the **IAggregatePartner.Customers** collection and call **ById** method with the specified customer identifier.</span></span>

- <span data-ttu-id="0d01a-121">Pegue na propriedade **Dos Contratos** e filtre os resultados para o Microsoft Cloud Agreement chamando o método **ByAgreementType.**</span><span class="sxs-lookup"><span data-stu-id="0d01a-121">Fetch the **Agreements** property and filter the results to Microsoft Cloud Agreement by calling **ByAgreementType** method.</span></span>

- <span data-ttu-id="0d01a-122">Ligue para o método **Get** ou **GetAsync.**</span><span class="sxs-lookup"><span data-stu-id="0d01a-122">Call **Get** or **GetAsync** method.</span></span>

```csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;

string agreementType = "MicrosoftCloudAgreement";

var cloudAgreements = partnerOperations.Customers.ById(selectedCustomerId).Agreements.ByAgreementType(agreementType).Get();
```

<span data-ttu-id="0d01a-123">Uma amostra completa pode ser encontrada na classe [GetCustomerAgreements](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/GetCustomerAgreements.cs) do projeto de [aplicações de teste](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples) de consola.</span><span class="sxs-lookup"><span data-stu-id="0d01a-123">A complete sample can be found in the [GetCustomerAgreements](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/GetCustomerAgreements.cs) class from the [console test app](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples) project.</span></span>

## <a name="net-version-19---113"></a><span data-ttu-id="0d01a-124">.NET (versão 1.9 - 1.13)</span><span class="sxs-lookup"><span data-stu-id="0d01a-124">.NET (version 1.9 - 1.13)</span></span>

<span data-ttu-id="0d01a-125">Para obter a confirmação da aceitação do cliente fornecida anteriormente:</span><span class="sxs-lookup"><span data-stu-id="0d01a-125">To retrieve confirmation of customer acceptance provided previously:</span></span>

<span data-ttu-id="0d01a-126">Utilize a recolha **IAggregatePartner.Customers** e ligue para o método **ById** com o identificador do cliente especificado.</span><span class="sxs-lookup"><span data-stu-id="0d01a-126">Use the **IAggregatePartner.Customers** collection and call the **ById** method with the specified customer's identifier.</span></span> <span data-ttu-id="0d01a-127">Em seguida, obtenha a propriedade **Dos Acordos,** seguida de chamar os métodos **Get** ou **GetAsync.**</span><span class="sxs-lookup"><span data-stu-id="0d01a-127">Then, get the **Agreements** property, followed by calling the **Get** or **GetAsync** methods.</span></span>

```csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;

var agreements = partnerOperations.Customers.ById(selectedCustomerId).Agreements.Get();
```

## <a name="java"></a><span data-ttu-id="0d01a-128">Java</span><span class="sxs-lookup"><span data-stu-id="0d01a-128">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="0d01a-129">Para obter a confirmação da aceitação do cliente fornecida anteriormente:</span><span class="sxs-lookup"><span data-stu-id="0d01a-129">To retrieve confirmation of customer acceptance provided previously:</span></span>

<span data-ttu-id="0d01a-130">Utilize a função **IAggregatePartner.getCustomers** e ligue para a função **byId** com o identificador do cliente especificado.</span><span class="sxs-lookup"><span data-stu-id="0d01a-130">Use the **IAggregatePartner.getCustomers** function and call the **byId** function with the specified customer's identifier.</span></span> <span data-ttu-id="0d01a-131">Em seguida, obtenha a função **getAgreements,** seguido chamando a função **get.**</span><span class="sxs-lookup"><span data-stu-id="0d01a-131">Then, get the **getAgreements** function, followed by calling the **get** function.</span></span>

```java
// IAggregatePartner partnerOperations;
// String selectedCustomerId;

ResourceCollection<Agreement> agreements = partnerOperations.getCustomers().byId(selectedCustomerId).getAgreements().get();
```

<span data-ttu-id="0d01a-132">Uma amostra completa pode ser encontrada na classe [GetCustomerAgreements](https://github.com/microsoft/Partner-Center-Java-Samples/blob/master/sdk/src/main/java/com/microsoft/store/partnercenter/samples/agreements/GetCustomerAgreements.java) do projeto de [aplicações de teste](https://github.com/Microsoft/Partner-Center-Java-Samples) de consola.</span><span class="sxs-lookup"><span data-stu-id="0d01a-132">A complete sample can be found in the [GetCustomerAgreements](https://github.com/microsoft/Partner-Center-Java-Samples/blob/master/sdk/src/main/java/com/microsoft/store/partnercenter/samples/agreements/GetCustomerAgreements.java) class from the [console test app](https://github.com/Microsoft/Partner-Center-Java-Samples) project.</span></span>

## <a name="powershell"></a><span data-ttu-id="0d01a-133">PowerShell</span><span class="sxs-lookup"><span data-stu-id="0d01a-133">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="0d01a-134">Para obter a confirmação da aceitação do cliente fornecida anteriormente:</span><span class="sxs-lookup"><span data-stu-id="0d01a-134">To retrieve confirmation of customer acceptance provided previously:</span></span>

<span data-ttu-id="0d01a-135">Utilize o comando [**Get-PartnerCustomerAgreement.**](/powershell/module/partnercenter/get-partnercustomeragreement)</span><span class="sxs-lookup"><span data-stu-id="0d01a-135">Use the [**Get-PartnerCustomerAgreement**](/powershell/module/partnercenter/get-partnercustomeragreement) command.</span></span>

```powershell
Get-PartnerCustomerAgreement -CustomerId '14876998-c0dc-46e6-9d0c-65a57a6c32ec'
```

## <a name="rest-request"></a><span data-ttu-id="0d01a-136">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="0d01a-136">REST request</span></span>

<span data-ttu-id="0d01a-137">Para obter a confirmação da aceitação do cliente fornecida anteriormente, consulte as seguintes instruções.</span><span class="sxs-lookup"><span data-stu-id="0d01a-137">To retrieve confirmation of customer acceptance provided previously, see the following instructions.</span></span>

<span data-ttu-id="0d01a-138">Criar um novo recurso **do Acordo** com as informações de certificação relevantes.</span><span class="sxs-lookup"><span data-stu-id="0d01a-138">Create a new **Agreement** resource with the relevant certification information.</span></span>

### <a name="request-syntax"></a><span data-ttu-id="0d01a-139">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="0d01a-139">Request syntax</span></span>

| <span data-ttu-id="0d01a-140">Método</span><span class="sxs-lookup"><span data-stu-id="0d01a-140">Method</span></span> | <span data-ttu-id="0d01a-141">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="0d01a-141">Request URI</span></span>                                                                                      |
|--------|--------------------------------------------------------------------------------------------------|
| <span data-ttu-id="0d01a-142">GET</span><span class="sxs-lookup"><span data-stu-id="0d01a-142">GET</span></span>    | <span data-ttu-id="0d01a-143">[*\{ baseURL \}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/acordos HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="0d01a-143">[*\{baseURL\}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/agreements HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="0d01a-144">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="0d01a-144">URI parameter</span></span>

<span data-ttu-id="0d01a-145">Utilize o seguinte parâmetro de consulta para especificar o cliente que está a confirmar.</span><span class="sxs-lookup"><span data-stu-id="0d01a-145">Use the following query parameter to specify the customer you are confirming.</span></span>

| <span data-ttu-id="0d01a-146">Nome</span><span class="sxs-lookup"><span data-stu-id="0d01a-146">Name</span></span>             | <span data-ttu-id="0d01a-147">Tipo</span><span class="sxs-lookup"><span data-stu-id="0d01a-147">Type</span></span> | <span data-ttu-id="0d01a-148">Necessário</span><span class="sxs-lookup"><span data-stu-id="0d01a-148">Required</span></span> | <span data-ttu-id="0d01a-149">Descrição</span><span class="sxs-lookup"><span data-stu-id="0d01a-149">Description</span></span>                                                                               |
|------------------|------|----------|-------------------------------------------------------------------------------------------|
| <span data-ttu-id="0d01a-150">CustomerTenantId</span><span class="sxs-lookup"><span data-stu-id="0d01a-150">CustomerTenantId</span></span> | <span data-ttu-id="0d01a-151">GUID</span><span class="sxs-lookup"><span data-stu-id="0d01a-151">GUID</span></span> | <span data-ttu-id="0d01a-152">Y</span><span class="sxs-lookup"><span data-stu-id="0d01a-152">Y</span></span>        | <span data-ttu-id="0d01a-153">O valor é um **CustomerTenantId** formatado guid que lhe permite especificar um cliente.</span><span class="sxs-lookup"><span data-stu-id="0d01a-153">The value is a GUID formatted **CustomerTenantId** that allows you to specify a customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="0d01a-154">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="0d01a-154">Request headers</span></span>

<span data-ttu-id="0d01a-155">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="0d01a-155">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="0d01a-156">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="0d01a-156">Request body</span></span>

<span data-ttu-id="0d01a-157">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="0d01a-157">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="0d01a-158">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="0d01a-158">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/14876998-c0dc-46e6-9d0c-65a57a6c32ec/agreements HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
```

## <a name="rest-response"></a><span data-ttu-id="0d01a-159">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="0d01a-159">REST response</span></span>

<span data-ttu-id="0d01a-160">Se for bem sucedido, este método devolve uma recolha de recursos do **Acordo** no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="0d01a-160">If successful, this method returns a collection of **Agreement** resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="0d01a-161">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="0d01a-161">Response success and error codes</span></span>

<span data-ttu-id="0d01a-162">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="0d01a-162">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="0d01a-163">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="0d01a-163">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="0d01a-164">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="0d01a-164">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="0d01a-165">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="0d01a-165">Response example</span></span>

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
                "email":"SomeEmail@Outlook.com"
                "phoneNumber":"1234567890"
            },
            "templateId":"998b88de-aa99-4388-a42c-1b3517d49490",
            "dateAgreed":"2018-07-28T00:00:00",
            "type":"MicrosoftCloudAgreement",
            "agreementLink":"https://docs.microsoft.com/partner-center/agreements"
        },
        {
            "primaryContact":
            {
                "firstName":"Tania",
                "lastName":"Carr",
                "email":"SomeEmail@Outlook.com"
                "phoneNumber:"1234567890"
            },
            "templateId":"998b88de-aa99-4388-a42c-1b3517d49490",
            "dateAgreed":"2017-08-01T00:00:00",
            "type":"MicrosoftCloudAgreement",
            "agreementLink":"https://docs.microsoft.com/partner-center/agreements"
        }
    ]
}
```
