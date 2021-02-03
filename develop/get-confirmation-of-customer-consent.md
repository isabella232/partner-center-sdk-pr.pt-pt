---
title: Obter confirmação da aceitação do cliente do Contrato da Microsoft Cloud
description: Este artigo explica como obter a confirmação da aceitação pelo cliente do Microsoft Cloud Agreement.
ms.date: 02/12/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
aauthor: khakiali
ms.author: alikhaki
ms.openlocfilehash: d91f70cbd8bc9b8622b8d41ab9e601e2aee2cfab
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/19/2020
ms.locfileid: "97769859"
---
# <a name="get-confirmation-of-customer-acceptance-of-microsoft-cloud-agreement"></a><span data-ttu-id="2fbfa-103">Obter confirmação da aceitação do cliente do Contrato da Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="2fbfa-103">Get confirmation of customer acceptance of Microsoft Cloud Agreement</span></span>

<span data-ttu-id="2fbfa-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="2fbfa-104">**Applies To**</span></span>

- <span data-ttu-id="2fbfa-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="2fbfa-105">Partner Center</span></span>

> [!NOTE]
> <span data-ttu-id="2fbfa-106">O recurso **Do Acordo** é atualmente suportado pelo Partner Center apenas na nuvem pública da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="2fbfa-106">The **Agreement** resource is currently supported by Partner Center in the Microsoft public cloud only.</span></span> <span data-ttu-id="2fbfa-107">Não é aplicável a:</span><span class="sxs-lookup"><span data-stu-id="2fbfa-107">It isn't applicable to:</span></span>
>
> - <span data-ttu-id="2fbfa-108">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="2fbfa-108">Partner Center operated by 21Vianet</span></span>
> - <span data-ttu-id="2fbfa-109">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="2fbfa-109">Partner Center for Microsoft Cloud Germany</span></span>
> - <span data-ttu-id="2fbfa-110">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="2fbfa-110">Partner Center for Microsoft Cloud for US Government</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2fbfa-111">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="2fbfa-111">Prerequisites</span></span>

- <span data-ttu-id="2fbfa-112">Se estiver a utilizar o Partner Center .NET SDK, é necessária a versão 1.9 ou a mais recente.</span><span class="sxs-lookup"><span data-stu-id="2fbfa-112">If you are using the Partner Center .NET SDK, version 1.9 or newer is required.</span></span>

- <span data-ttu-id="2fbfa-113">Se estiver a utilizar o Partner Center Java SDK, é necessária a versão 1.8 ou mais recente.</span><span class="sxs-lookup"><span data-stu-id="2fbfa-113">If you are using the Partner Center Java SDK, version 1.8 or newer is required.</span></span>

- <span data-ttu-id="2fbfa-114">Credenciais descritas na [autenticação do Partner Center](./partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="2fbfa-114">Credentials as described in [Partner Center authentication](./partner-center-authentication.md).</span></span> <span data-ttu-id="2fbfa-115">Este cenário suporta apenas a app + autenticação do utilizador.</span><span class="sxs-lookup"><span data-stu-id="2fbfa-115">This scenario supports only supports app + user authentication.</span></span>

- <span data-ttu-id="2fbfa-116">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="2fbfa-116">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="2fbfa-117">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="2fbfa-117">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="2fbfa-118">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="2fbfa-118">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="2fbfa-119">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="2fbfa-119">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="2fbfa-120">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="2fbfa-120">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="2fbfa-121">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="2fbfa-121">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="net-version-14-or-newer"></a><span data-ttu-id="2fbfa-122">.NET (versão 1.4 ou mais recente)</span><span class="sxs-lookup"><span data-stu-id="2fbfa-122">.NET (version 1.4 or newer)</span></span>

<span data-ttu-id="2fbfa-123">Para obter confirmação(s) de aceitação do cliente que foi previamente fornecida:</span><span class="sxs-lookup"><span data-stu-id="2fbfa-123">To retrieve confirmation(s) of customer acceptance that was previously provided:</span></span>

- <span data-ttu-id="2fbfa-124">Utilize a recolha **IAggregatePartner.Customers** e ligue para o método **ById** com o identificador de clientes especificado.</span><span class="sxs-lookup"><span data-stu-id="2fbfa-124">Use the **IAggregatePartner.Customers** collection and call **ById** method with the specified customer identifier.</span></span>

- <span data-ttu-id="2fbfa-125">Pegue na propriedade **Dos Contratos** e filtre os resultados para o Microsoft Cloud Agreement chamando o método **ByAgreementType.**</span><span class="sxs-lookup"><span data-stu-id="2fbfa-125">Fetch the **Agreements** property and filter the results to Microsoft Cloud Agreement by calling **ByAgreementType** method.</span></span>

- <span data-ttu-id="2fbfa-126">Ligue para o método **Get** ou **GetAsync.**</span><span class="sxs-lookup"><span data-stu-id="2fbfa-126">Call **Get** or **GetAsync** method.</span></span>

```csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;

string agreementType = "MicrosoftCloudAgreement";

var cloudAgreements = partnerOperations.Customers.ById(selectedCustomerId).Agreements.ByAgreementType(agreementType).Get();
```

<span data-ttu-id="2fbfa-127">Uma amostra completa pode ser encontrada na classe [GetCustomerAgreements](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/GetCustomerAgreements.cs) do projeto de [aplicações de teste](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples) de consola.</span><span class="sxs-lookup"><span data-stu-id="2fbfa-127">A complete sample can be found in the [GetCustomerAgreements](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/GetCustomerAgreements.cs) class from the [console test app](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples) project.</span></span>

## <a name="net-version-19---113"></a><span data-ttu-id="2fbfa-128">.NET (versão 1.9 - 1.13)</span><span class="sxs-lookup"><span data-stu-id="2fbfa-128">.NET (version 1.9 - 1.13)</span></span>

<span data-ttu-id="2fbfa-129">Para obter a confirmação da aceitação do cliente fornecida anteriormente:</span><span class="sxs-lookup"><span data-stu-id="2fbfa-129">To retrieve confirmation of customer acceptance provided previously:</span></span>

<span data-ttu-id="2fbfa-130">Utilize a recolha **IAggregatePartner.Customers** e ligue para o método **ById** com o identificador do cliente especificado.</span><span class="sxs-lookup"><span data-stu-id="2fbfa-130">Use the **IAggregatePartner.Customers** collection and call the **ById** method with the specified customer's identifier.</span></span> <span data-ttu-id="2fbfa-131">Em seguida, obtenha a propriedade **Dos Acordos,** seguida de chamar os métodos **Get** ou **GetAsync.**</span><span class="sxs-lookup"><span data-stu-id="2fbfa-131">Then, get the **Agreements** property, followed by calling the **Get** or **GetAsync** methods.</span></span>

```csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;

var agreements = partnerOperations.Customers.ById(selectedCustomerId).Agreements.Get();
```

## <a name="java"></a><span data-ttu-id="2fbfa-132">Java</span><span class="sxs-lookup"><span data-stu-id="2fbfa-132">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="2fbfa-133">Para obter a confirmação da aceitação do cliente fornecida anteriormente:</span><span class="sxs-lookup"><span data-stu-id="2fbfa-133">To retrieve confirmation of customer acceptance provided previously:</span></span>

<span data-ttu-id="2fbfa-134">Utilize a função **IAggregatePartner.getCustomers** e ligue para a função **byId** com o identificador do cliente especificado.</span><span class="sxs-lookup"><span data-stu-id="2fbfa-134">Use the **IAggregatePartner.getCustomers** function and call the **byId** function with the specified customer's identifier.</span></span> <span data-ttu-id="2fbfa-135">Em seguida, obtenha a função **getAgreements,** seguido chamando a função **get.**</span><span class="sxs-lookup"><span data-stu-id="2fbfa-135">Then, get the **getAgreements** function, followed by calling the **get** function.</span></span>

```java
// IAggregatePartner partnerOperations;
// String selectedCustomerId;

ResourceCollection<Agreement> agreements = partnerOperations.getCustomers().byId(selectedCustomerId).getAgreements().get();
```

<span data-ttu-id="2fbfa-136">Uma amostra completa pode ser encontrada na classe [GetCustomerAgreements](https://github.com/microsoft/Partner-Center-Java-Samples/blob/master/sdk/src/main/java/com/microsoft/store/partnercenter/samples/agreements/GetCustomerAgreements.java) do projeto de [aplicações de teste](https://github.com/Microsoft/Partner-Center-Java-Samples) de consola.</span><span class="sxs-lookup"><span data-stu-id="2fbfa-136">A complete sample can be found in the [GetCustomerAgreements](https://github.com/microsoft/Partner-Center-Java-Samples/blob/master/sdk/src/main/java/com/microsoft/store/partnercenter/samples/agreements/GetCustomerAgreements.java) class from the [console test app](https://github.com/Microsoft/Partner-Center-Java-Samples) project.</span></span>

## <a name="powershell"></a><span data-ttu-id="2fbfa-137">PowerShell</span><span class="sxs-lookup"><span data-stu-id="2fbfa-137">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="2fbfa-138">Para obter a confirmação da aceitação do cliente fornecida anteriormente:</span><span class="sxs-lookup"><span data-stu-id="2fbfa-138">To retrieve confirmation of customer acceptance provided previously:</span></span>

<span data-ttu-id="2fbfa-139">Utilize o comando [**Get-PartnerCustomerAgreement.**](/powershell/module/partnercenter/get-partnercustomeragreement)</span><span class="sxs-lookup"><span data-stu-id="2fbfa-139">Use the [**Get-PartnerCustomerAgreement**](/powershell/module/partnercenter/get-partnercustomeragreement) command.</span></span>

```powershell
Get-PartnerCustomerAgreement -CustomerId '14876998-c0dc-46e6-9d0c-65a57a6c32ec'
```

## <a name="rest-request"></a><span data-ttu-id="2fbfa-140">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="2fbfa-140">REST request</span></span>

<span data-ttu-id="2fbfa-141">Para obter a confirmação da aceitação do cliente fornecida anteriormente, consulte as seguintes instruções.</span><span class="sxs-lookup"><span data-stu-id="2fbfa-141">To retrieve confirmation of customer acceptance provided previously, see the following instructions.</span></span>

<span data-ttu-id="2fbfa-142">Criar um novo recurso **do Acordo** com as informações de certificação relevantes.</span><span class="sxs-lookup"><span data-stu-id="2fbfa-142">Create a new **Agreement** resource with the relevant certification information.</span></span>

### <a name="request-syntax"></a><span data-ttu-id="2fbfa-143">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="2fbfa-143">Request syntax</span></span>

| <span data-ttu-id="2fbfa-144">Método</span><span class="sxs-lookup"><span data-stu-id="2fbfa-144">Method</span></span> | <span data-ttu-id="2fbfa-145">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="2fbfa-145">Request URI</span></span>                                                                                      |
|--------|--------------------------------------------------------------------------------------------------|
| <span data-ttu-id="2fbfa-146">GET</span><span class="sxs-lookup"><span data-stu-id="2fbfa-146">GET</span></span>    | <span data-ttu-id="2fbfa-147">[*\{ baseURL \}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/acordos HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="2fbfa-147">[*\{baseURL\}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/agreements HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="2fbfa-148">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="2fbfa-148">URI parameter</span></span>

<span data-ttu-id="2fbfa-149">Utilize o seguinte parâmetro de consulta para especificar o cliente que está a confirmar.</span><span class="sxs-lookup"><span data-stu-id="2fbfa-149">Use the following query parameter to specify the customer you are confirming.</span></span>

| <span data-ttu-id="2fbfa-150">Nome</span><span class="sxs-lookup"><span data-stu-id="2fbfa-150">Name</span></span>             | <span data-ttu-id="2fbfa-151">Tipo</span><span class="sxs-lookup"><span data-stu-id="2fbfa-151">Type</span></span> | <span data-ttu-id="2fbfa-152">Necessário</span><span class="sxs-lookup"><span data-stu-id="2fbfa-152">Required</span></span> | <span data-ttu-id="2fbfa-153">Descrição</span><span class="sxs-lookup"><span data-stu-id="2fbfa-153">Description</span></span>                                                                               |
|------------------|------|----------|-------------------------------------------------------------------------------------------|
| <span data-ttu-id="2fbfa-154">CustomerTenantId</span><span class="sxs-lookup"><span data-stu-id="2fbfa-154">CustomerTenantId</span></span> | <span data-ttu-id="2fbfa-155">GUID</span><span class="sxs-lookup"><span data-stu-id="2fbfa-155">GUID</span></span> | <span data-ttu-id="2fbfa-156">Y</span><span class="sxs-lookup"><span data-stu-id="2fbfa-156">Y</span></span>        | <span data-ttu-id="2fbfa-157">O valor é um **CustomerTenantId** formatado guid que lhe permite especificar um cliente.</span><span class="sxs-lookup"><span data-stu-id="2fbfa-157">The value is a GUID formatted **CustomerTenantId** that allows you to specify a customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="2fbfa-158">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="2fbfa-158">Request headers</span></span>

<span data-ttu-id="2fbfa-159">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="2fbfa-159">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="2fbfa-160">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="2fbfa-160">Request body</span></span>

<span data-ttu-id="2fbfa-161">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="2fbfa-161">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="2fbfa-162">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="2fbfa-162">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/14876998-c0dc-46e6-9d0c-65a57a6c32ec/agreements HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
```

## <a name="rest-response"></a><span data-ttu-id="2fbfa-163">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="2fbfa-163">REST response</span></span>

<span data-ttu-id="2fbfa-164">Se for bem sucedido, este método devolve uma recolha de recursos do **Acordo** no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="2fbfa-164">If successful, this method returns a collection of **Agreement** resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="2fbfa-165">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="2fbfa-165">Response success and error codes</span></span>

<span data-ttu-id="2fbfa-166">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="2fbfa-166">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="2fbfa-167">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="2fbfa-167">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="2fbfa-168">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="2fbfa-168">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="2fbfa-169">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="2fbfa-169">Response example</span></span>

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
