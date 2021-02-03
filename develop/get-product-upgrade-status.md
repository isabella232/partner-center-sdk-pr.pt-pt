---
title: Obtenha o estado de atualização do produto para um cliente
description: Pode utilizar o recurso ProductUpgradeRequest para determinar o estado de uma atualização do produto para um cliente para uma nova família de produtos, como por exemplo a partir de uma assinatura Microsoft Azure (MS-AZR-0145P) para um plano Azure.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 1819887d459ec72a48ea2b7a5a4121dc56718313
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97769061"
---
# <a name="get-the-product-upgrade-status-for-a-customer"></a><span data-ttu-id="ceab4-103">Obtenha o estado de atualização do produto para um cliente</span><span class="sxs-lookup"><span data-stu-id="ceab4-103">Get the product upgrade status for a customer</span></span>

<span data-ttu-id="ceab4-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="ceab4-104">**Applies to:**</span></span>

- <span data-ttu-id="ceab4-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="ceab4-105">Partner Center</span></span>

<span data-ttu-id="ceab4-106">Pode utilizar o recurso [**ProductUpgradeRequest**](product-upgrade-resources.md#productupgraderequest) para obter o estado de uma atualização para uma nova família de produtos.</span><span class="sxs-lookup"><span data-stu-id="ceab4-106">You can use the [**ProductUpgradeRequest**](product-upgrade-resources.md#productupgraderequest) resource to get the status of an upgrade to a new product family.</span></span> <span data-ttu-id="ceab4-107">Este recurso aplica-se quando está a atualizar um cliente a partir de uma subscrição do Microsoft Azure (MS-AZR-0145P) para um plano Azure.</span><span class="sxs-lookup"><span data-stu-id="ceab4-107">This resource applies when you're upgrading a customer from an Microsoft Azure (MS-AZR-0145P) subscription to an Azure plan.</span></span> <span data-ttu-id="ceab4-108">Um pedido bem sucedido devolve o recurso [**de melhoria de produtos.**](product-upgrade-resources.md#productupgradeseligibility)</span><span class="sxs-lookup"><span data-stu-id="ceab4-108">A successful request returns the [**ProductUpgradesEligibility**](product-upgrade-resources.md#productupgradeseligibility) resource.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ceab4-109">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="ceab4-109">Prerequisites</span></span>

- <span data-ttu-id="ceab4-110">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="ceab4-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="ceab4-111">Este cenário suporta a autenticação com credenciais app+utilizador.</span><span class="sxs-lookup"><span data-stu-id="ceab4-111">This scenario supports authentication with App+User credentials.</span></span> <span data-ttu-id="ceab4-112">Siga o [modelo de aplicação seguro](enable-secure-app-model.md) ao utilizar a autenticação App+User com APIs do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="ceab4-112">Follow the [secure app model](enable-secure-app-model.md) when using App+User authentication with Partner Center APIs.</span></span>

- <span data-ttu-id="ceab4-113">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="ceab4-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="ceab4-114">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="ceab4-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="ceab4-115">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="ceab4-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="ceab4-116">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="ceab4-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="ceab4-117">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="ceab4-117">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="ceab4-118">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="ceab4-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="ceab4-119">A família dos produtos.</span><span class="sxs-lookup"><span data-stu-id="ceab4-119">The product family.</span></span>

- <span data-ttu-id="ceab4-120">O upgrade de um pedido de upgrade.</span><span class="sxs-lookup"><span data-stu-id="ceab4-120">The upgrade-id of an upgrade request.</span></span>

## <a name="c"></a><span data-ttu-id="ceab4-121">C\#</span><span class="sxs-lookup"><span data-stu-id="ceab4-121">C\#</span></span>

<span data-ttu-id="ceab4-122">Para verificar se um cliente é elegível para fazer upgrade para o plano Azure:</span><span class="sxs-lookup"><span data-stu-id="ceab4-122">To check if a customer is eligible to upgrade to Azure plan:</span></span>

1. <span data-ttu-id="ceab4-123">Crie um objeto **ProductUpgradesRequest** e especifique o identificador do cliente e o "Azure" como a família do produto.</span><span class="sxs-lookup"><span data-stu-id="ceab4-123">Create a **ProductUpgradesRequest** object and specify the customer identifier and "Azure" as the product family.</span></span>

2. <span data-ttu-id="ceab4-124">Utilize a coleção **IAggregatePartner.ProductUpgrades.**</span><span class="sxs-lookup"><span data-stu-id="ceab4-124">Use the **IAggregatePartner.ProductUpgrades** collection.</span></span>

3. <span data-ttu-id="ceab4-125">Ligue para o método **ById** e passe no **upgrade-id**.</span><span class="sxs-lookup"><span data-stu-id="ceab4-125">Call the **ById** method and pass in the **upgrade-id**.</span></span>

4. <span data-ttu-id="ceab4-126">Ligue para o método **CheckStatus** e passe no objeto **ProductUpgradesRequest,** que devolverá um objeto **ProductUpgradeStatus.**</span><span class="sxs-lookup"><span data-stu-id="ceab4-126">Call the **CheckStatus** method and pass in the **ProductUpgradesRequest** object, which will return a **ProductUpgradeStatus** object.</span></span>

```csharp
// IAggregatePartner partnerOperations;

string selectedCustomerId = "58e2af4f-0ad3-4688-8744-be2357cd939a";

string selectedProductFamily = "azure";

var productUpgradeRequest = new ProductUpgradesRequest
{
    CustomerId = selectedCustomerId,
    ProductFamily = selectedProductFamily
};

ProductUpgradesStatus productUpgradeStatus = partnerOperations.ProductUpgrades.ById(selectedUpgradeId).CheckStatus(productUpgradeRequest);

if (productUpgradeEligibility.IsEligibile)
{
    ....
}

```

## <a name="rest-request"></a><span data-ttu-id="ceab4-127">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="ceab4-127">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="ceab4-128">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="ceab4-128">Request syntax</span></span>

| <span data-ttu-id="ceab4-129">Método</span><span class="sxs-lookup"><span data-stu-id="ceab4-129">Method</span></span>   | <span data-ttu-id="ceab4-130">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="ceab4-130">Request URI</span></span> |
|----------|-----------------------------------------------------------------------------------------------|
| <span data-ttu-id="ceab4-131">**Publicar**</span><span class="sxs-lookup"><span data-stu-id="ceab4-131">**POST**</span></span> | <span data-ttu-id="ceab4-132">[*{baseURL}*](partner-center-rest-urls.md)/v1/productUpgrades/{upgrade-id}/status HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="ceab4-132">[*{baseURL}*](partner-center-rest-urls.md)/v1/productUpgrades/{upgrade-id}/status HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="ceab4-133">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="ceab4-133">URI parameter</span></span>

<span data-ttu-id="ceab4-134">Utilize o seguinte parâmetro de consulta para especificar o cliente para o qual está a obter um estado de atualização do produto.</span><span class="sxs-lookup"><span data-stu-id="ceab4-134">Use the following query parameter to specify the customer for whom you're getting a product upgrade status.</span></span>

| <span data-ttu-id="ceab4-135">Nome</span><span class="sxs-lookup"><span data-stu-id="ceab4-135">Name</span></span>               | <span data-ttu-id="ceab4-136">Tipo</span><span class="sxs-lookup"><span data-stu-id="ceab4-136">Type</span></span> | <span data-ttu-id="ceab4-137">Necessário</span><span class="sxs-lookup"><span data-stu-id="ceab4-137">Required</span></span> | <span data-ttu-id="ceab4-138">Descrição</span><span class="sxs-lookup"><span data-stu-id="ceab4-138">Description</span></span>                                                                                 |
|--------------------|------|----------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="ceab4-139">**upgrade-id**</span><span class="sxs-lookup"><span data-stu-id="ceab4-139">**upgrade-id**</span></span> | <span data-ttu-id="ceab4-140">GUID</span><span class="sxs-lookup"><span data-stu-id="ceab4-140">GUID</span></span> | <span data-ttu-id="ceab4-141">Sim</span><span class="sxs-lookup"><span data-stu-id="ceab4-141">Yes</span></span> | <span data-ttu-id="ceab4-142">O valor é um identificador de upgrade formatado guid.</span><span class="sxs-lookup"><span data-stu-id="ceab4-142">The value is a GUID-formatted upgrade identifier.</span></span> <span data-ttu-id="ceab4-143">Pode utilizar este identificador para especificar uma atualização para rastrear.</span><span class="sxs-lookup"><span data-stu-id="ceab4-143">You can use this identifier to specify an upgrade to track.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="ceab4-144">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="ceab4-144">Request headers</span></span>

<span data-ttu-id="ceab4-145">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="ceab4-145">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="ceab4-146">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="ceab4-146">Request body</span></span>

<span data-ttu-id="ceab4-147">O organismo de pedido deve conter um recurso [**ProductUpgradeRequest.**](product-upgrade-resources.md#productupgraderequest)</span><span class="sxs-lookup"><span data-stu-id="ceab4-147">The request body must contain a [**ProductUpgradeRequest**](product-upgrade-resources.md#productupgraderequest) resource.</span></span>

### <a name="request-example"></a><span data-ttu-id="ceab4-148">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="ceab4-148">Request example</span></span>

```http
POST https://api.partnercenter.microsoft.com/v1/productupgrades/42d075a4-bfe7-43e7-af6d-7c68a57edcb4/status  HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: c245d5f2-1de3-4ae0-9e42-95e38e3cb8ff
MS-CorrelationId: e3f26e6a-044f-4371-ad52-0d91ce4200be
X-Locale: en-US
MS-PartnerCenter-Application: Partner Center .NET SDK Samples
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 340
Expect: 100-continue
Connection: Keep-Alive
{
 {
    "customerId": "4c721420-72ad-4708-a0a7-371a2f7b0969",
    "productFamily": "azure"
  }
  "Attributes": {
  "ObjectType": "ProductUpgradeRequest"
  }
}
```

## <a name="rest-response"></a><span data-ttu-id="ceab4-149">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="ceab4-149">REST response</span></span>

<span data-ttu-id="ceab4-150">Se for bem sucedido, este método devolve um recurso [**de melhoria de identidade do produto**](product-upgrade-resources.md#productupgradeseligibility) no organismo.</span><span class="sxs-lookup"><span data-stu-id="ceab4-150">If successful, this method returns a [**ProductUpgradesEligibility**](product-upgrade-resources.md#productupgradeseligibility) resource in the body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="ceab4-151">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="ceab4-151">Response success and error codes</span></span>

<span data-ttu-id="ceab4-152">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="ceab4-152">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="ceab4-153">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="ceab4-153">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="ceab4-154">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="ceab4-154">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="ceab4-155">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="ceab4-155">Response example</span></span>

```http
HTTP/1.1 200 Ok
Content-Length: 150
MS-CorrelationId: 772871a9-399b-4f3b-b8c7-38f550e4f22a
MS-RequestId: cb82f7d6-f0d9-44d4-82f9-f6eee6e68390
MS-CV: iqOqN0FnaE2y0HcD.0
MS-ServerId: 030020525
Date: Thu, 04 Oct 2019 20:35:35 GMT

{
    "id": "42d075a4-bfe7-43e7-af6d-7c68a57edcb4",
    "status": "Completed",
    "productFamily": "Azure",
    "lineItems": [
        {
            "sourceProduct": {
                "id": "b1beb621-3cad-4d7a-b360-62db33ce028e",
                "name": "AzureSubscription"
            },
            "targetProduct": {
                "id": "d231908e-31c1-de0e-027b-bc5ce11f09d9",
                "name": "Microsoft Azure plan"
            },
            "upgradedDate": "2019-08-29T23:47:28.8524555Z",
            "status": "Completed"
        }
    ]
}

```
