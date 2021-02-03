---
title: Verifique a elegibilidade de um cliente para a atualização de um plano Azure
description: Pode utilizar o recurso ProductUpgradeRequest para devolver um recurso de melhoria de produtos para determinar se um cliente é elegível para atualizar a partir de uma subscrição do Microsoft Azure (MS-AZR-0145P) para um plano Azure.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: 568ed3f4cff7d9cd520e608d43cb89bb78e00ccc
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97768725"
---
# <a name="check-a-customers-eligibility-for-upgrading-to-an-azure-plan"></a><span data-ttu-id="3b133-103">Verifique a elegibilidade de um cliente para a atualização de um plano Azure</span><span class="sxs-lookup"><span data-stu-id="3b133-103">Check a customer's eligibility for upgrading to an Azure plan</span></span>

<span data-ttu-id="3b133-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="3b133-104">**Applies to:**</span></span>

- <span data-ttu-id="3b133-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="3b133-105">Partner Center</span></span>

<span data-ttu-id="3b133-106">Pode utilizar o recurso [**ProductUpgradeRequest**](product-upgrade-resources.md#productupgraderequest) para verificar se um cliente é elegível para atualizar para um plano Azure a partir de uma subscrição microsoft Azure (MS-AZR-0145P) Este método devolve um recurso [**de edição do Produto**](product-upgrade-resources.md#productupgradeseligibility) Com a elegibilidade do produto para upgrade do cliente.</span><span class="sxs-lookup"><span data-stu-id="3b133-106">You can use the [**ProductUpgradeRequest**](product-upgrade-resources.md#productupgraderequest) resource to check if a customer is eligible to upgrade to an Azure plan from a Microsoft Azure (MS-AZR-0145P) subscription This method returns a [**ProductUpgradesEligibility**](product-upgrade-resources.md#productupgradeseligibility) resource with the customer's product upgrade eligibility.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3b133-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="3b133-107">Prerequisites</span></span>

- <span data-ttu-id="3b133-108">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="3b133-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="3b133-109">Este cenário suporta a autenticação com credenciais app+utilizador.</span><span class="sxs-lookup"><span data-stu-id="3b133-109">This scenario supports authentication with App+User credentials.</span></span> <span data-ttu-id="3b133-110">Siga o [modelo de aplicação seguro](enable-secure-app-model.md) ao utilizar a autenticação App+User com APIs do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="3b133-110">Follow the [secure app model](enable-secure-app-model.md) when using App+User authentication with Partner Center APIs.</span></span>

- <span data-ttu-id="3b133-111">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="3b133-111">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="3b133-112">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="3b133-112">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="3b133-113">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="3b133-113">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="3b133-114">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="3b133-114">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="3b133-115">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="3b133-115">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="3b133-116">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="3b133-116">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="3b133-117">A família dos produtos.</span><span class="sxs-lookup"><span data-stu-id="3b133-117">The product family.</span></span>

## <a name="c"></a><span data-ttu-id="3b133-118">C\#</span><span class="sxs-lookup"><span data-stu-id="3b133-118">C\#</span></span>

<span data-ttu-id="3b133-119">Para verificar se um cliente é elegível para fazer upgrade para o plano Azure:</span><span class="sxs-lookup"><span data-stu-id="3b133-119">To check if a customer is eligible to upgrade to Azure plan:</span></span>

1. <span data-ttu-id="3b133-120">Crie um objeto **ProductUpgradesRequest** e especifique o identificador do cliente e o "Azure" como a família do produto.</span><span class="sxs-lookup"><span data-stu-id="3b133-120">Create a **ProductUpgradesRequest** object and specify the customer identifier and "Azure" as the product family.</span></span>

2. <span data-ttu-id="3b133-121">Utilize a coleção **IAggregatePartner.ProductUpgrades.**</span><span class="sxs-lookup"><span data-stu-id="3b133-121">Use the **IAggregatePartner.ProductUpgrades** collection.</span></span>
3. <span data-ttu-id="3b133-122">Ligue para o método **checkEelegibilidade** e passe no objeto **ProductUpgradesRequest,** que devolverá um objeto **de Melhoria de Produto.**</span><span class="sxs-lookup"><span data-stu-id="3b133-122">Call the **CheckEligibility** method and pass in the **ProductUpgradesRequest** object, which will return a **ProductUpgradesEligibility** object.</span></span>

```csharp
// IAggregatePartner partnerOperations;

string selectedCustomerId = "58e2af4f-0ad3-4688-8744-be2357cd939a";

string selectedProductFamily = "azure";

var productUpgradeRequest = new ProductUpgradesRequest
{
    CustomerId = selectedCustomerId,
    ProductFamily = selectedProductFamily
};

ProductUpgradesEligibility productUpgradeEligibility = partnerOperations.ProductUpgrades.CheckEligibility(productUpgradeRequest);

if (productUpgradeEligibility.IsEligibile)
{
    ....
}

```

## <a name="rest-request"></a><span data-ttu-id="3b133-123">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="3b133-123">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="3b133-124">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="3b133-124">Request syntax</span></span>

| <span data-ttu-id="3b133-125">Método</span><span class="sxs-lookup"><span data-stu-id="3b133-125">Method</span></span>   | <span data-ttu-id="3b133-126">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="3b133-126">Request URI</span></span>                                                                                   |
|----------|-----------------------------------------------------------------------------------------------|
| <span data-ttu-id="3b133-127">**Publicar**</span><span class="sxs-lookup"><span data-stu-id="3b133-127">**POST**</span></span> | <span data-ttu-id="3b133-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/productUpgrades/elegibilidade HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="3b133-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/productUpgrades/eligibility HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="3b133-129">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="3b133-129">Request headers</span></span>

<span data-ttu-id="3b133-130">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="3b133-130">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="3b133-131">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="3b133-131">Request body</span></span>

<span data-ttu-id="3b133-132">O organismo de pedido deve conter um recurso [**ProductUpgradeRequest.**](product-upgrade-resources.md#productupgraderequest)</span><span class="sxs-lookup"><span data-stu-id="3b133-132">The request body must contain a [**ProductUpgradeRequest**](product-upgrade-resources.md#productupgraderequest) resource.</span></span>

### <a name="request-example"></a><span data-ttu-id="3b133-133">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="3b133-133">Request example</span></span>

```http
POST https://api.partnercenter.microsoft.com/v1/productupgrades/eligibility HTTP/1.1
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
        "customerId": "4c721420-72ad-4708-a0a7-371a2f7b0969",
        "productFamily": "azure"
}
```

## <a name="rest-response"></a><span data-ttu-id="3b133-134">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="3b133-134">REST response</span></span>

<span data-ttu-id="3b133-135">Se for bem sucedido, este método devolve um recurso [**de melhoria de identidade do produto**](product-upgrade-resources.md#productupgradeseligibility) no organismo.</span><span class="sxs-lookup"><span data-stu-id="3b133-135">If successful, this method returns a [**ProductUpgradesEligibility**](product-upgrade-resources.md#productupgradeseligibility) resource in the body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="3b133-136">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="3b133-136">Response success and error codes</span></span>

<span data-ttu-id="3b133-137">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="3b133-137">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="3b133-138">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="3b133-138">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="3b133-139">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="3b133-139">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="3b133-140">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="3b133-140">Response example</span></span>

```http
HTTP/1.1 200 Ok
Content-Length: 150
MS-CorrelationId: 772871a9-399b-4f3b-b8c7-38f550e4f22a
MS-RequestId: cb82f7d6-f0d9-44d4-82f9-f6eee6e68390
MS-CV: iqOqN0FnaE2y0HcD.0
MS-ServerId: 030020525
Date: Thu, 04 Oct 2019 20:35:35 GMT

{
    "customerId": "c1958bc7-3284-4952-a257-de594ee64743",
    "isEligible": true,
    "productFamily": "azure"
}
```
