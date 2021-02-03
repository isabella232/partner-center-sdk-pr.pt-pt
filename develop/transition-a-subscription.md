---
title: Fazer a transição de uma subscrição
description: Atualiza a subscrição de um cliente para uma subscrição-alvo especificada.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 9b757eee8bc65c16b5c65221a4c14b6c0fd6369e
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97768936"
---
# <a name="transition-a-subscription"></a><span data-ttu-id="7892b-103">Fazer a transição de uma subscrição</span><span class="sxs-lookup"><span data-stu-id="7892b-103">Transition a subscription</span></span>

<span data-ttu-id="7892b-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="7892b-104">**Applies To**</span></span>

- <span data-ttu-id="7892b-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="7892b-105">Partner Center</span></span>
- <span data-ttu-id="7892b-106">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="7892b-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="7892b-107">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="7892b-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="7892b-108">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="7892b-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="7892b-109">Atualiza a subscrição de um cliente para uma subscrição-alvo especificada.</span><span class="sxs-lookup"><span data-stu-id="7892b-109">Upgrades a customer's subscription to a specified target subscription.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7892b-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="7892b-110">Prerequisites</span></span>

- <span data-ttu-id="7892b-111">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="7892b-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="7892b-112">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="7892b-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="7892b-113">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="7892b-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="7892b-114">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="7892b-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="7892b-115">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="7892b-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="7892b-116">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="7892b-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="7892b-117">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="7892b-117">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="7892b-118">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="7892b-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="7892b-119">Dois IDs de subscrição, um para a subscrição inicial e outro para a subscrição-alvo.</span><span class="sxs-lookup"><span data-stu-id="7892b-119">Two subscription IDs, one for the initial subscription and one for the target subscription.</span></span>

## <a name="c"></a><span data-ttu-id="7892b-120">C\#</span><span class="sxs-lookup"><span data-stu-id="7892b-120">C\#</span></span>

<span data-ttu-id="7892b-121">Para atualizar a subscrição de um cliente, primeiro [obtenha a subscrição do cliente.](get-a-subscription-by-id.md)</span><span class="sxs-lookup"><span data-stu-id="7892b-121">To upgrade a customer's subscription, first [get that's customer's subscription](get-a-subscription-by-id.md).</span></span> <span data-ttu-id="7892b-122">Em seguida, obtenha uma lista de atualizações para essa subscrição, chamando a propriedade Upgrades seguida pelos **métodos** **Get()** ou **GetAsync().**</span><span class="sxs-lookup"><span data-stu-id="7892b-122">Then, obtain a list of upgrades for that subscription by calling the **Upgrades** property followed by the **Get()** or **GetAsync()** methods.</span></span> <span data-ttu-id="7892b-123">Escolha uma atualização de destino a partir dessa lista de atualizações e, em seguida, chame a propriedade **upgrade da** subscrição inicial, seguida do método **Create().**</span><span class="sxs-lookup"><span data-stu-id="7892b-123">Choose a target upgrade from that list of upgrades, and then call the **Upgrades** property of the initial subscription, followed by the **Create()** method.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;
// string subscriptionIdForUpgrade;
// Upgrade targetOffer;

UpgradeResult upgradeResult = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(subscriptionIdForUpgrade).Upgrades.Create(targetOffer);
```

<span data-ttu-id="7892b-124">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="7892b-124">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="7892b-125">**Projeto**: PartnerSDK.FeatureSamples **Class**: UpgradeSubscription.cs</span><span class="sxs-lookup"><span data-stu-id="7892b-125">**Project**: PartnerSDK.FeatureSamples **Class**: UpgradeSubscription.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="7892b-126">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="7892b-126">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="7892b-127">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="7892b-127">Request syntax</span></span>

| <span data-ttu-id="7892b-128">Método</span><span class="sxs-lookup"><span data-stu-id="7892b-128">Method</span></span>   | <span data-ttu-id="7892b-129">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="7892b-129">Request URI</span></span>                                                                                                                         |
|----------|-------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="7892b-130">**Obter**</span><span class="sxs-lookup"><span data-stu-id="7892b-130">**GET**</span></span>  | <span data-ttu-id="7892b-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscrições/{id-for-subscription}/upgrades HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="7892b-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription}/upgrades HTTP/1.1</span></span> |
| <span data-ttu-id="7892b-132">**Publicar**</span><span class="sxs-lookup"><span data-stu-id="7892b-132">**POST**</span></span> | <span data-ttu-id="7892b-133">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/subscrições/{id-for-target}/upgrades HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="7892b-133">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{id-for-target}/upgrades HTTP/1.1</span></span>       |

### <a name="uri-parameter"></a><span data-ttu-id="7892b-134">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="7892b-134">URI parameter</span></span>

<span data-ttu-id="7892b-135">Utilize o seguinte parâmetro de consulta para a transição da subscrição.</span><span class="sxs-lookup"><span data-stu-id="7892b-135">Use the following query parameter to transition the subscription.</span></span>

| <span data-ttu-id="7892b-136">Nome</span><span class="sxs-lookup"><span data-stu-id="7892b-136">Name</span></span>                    | <span data-ttu-id="7892b-137">Tipo</span><span class="sxs-lookup"><span data-stu-id="7892b-137">Type</span></span>     | <span data-ttu-id="7892b-138">Necessário</span><span class="sxs-lookup"><span data-stu-id="7892b-138">Required</span></span> | <span data-ttu-id="7892b-139">Descrição</span><span class="sxs-lookup"><span data-stu-id="7892b-139">Description</span></span>                                       |
|-------------------------|----------|----------|---------------------------------------------------|
| <span data-ttu-id="7892b-140">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="7892b-140">**customer-tenant-id**</span></span>  | <span data-ttu-id="7892b-141">**guid**</span><span class="sxs-lookup"><span data-stu-id="7892b-141">**guid**</span></span> | <span data-ttu-id="7892b-142">Y</span><span class="sxs-lookup"><span data-stu-id="7892b-142">Y</span></span>        | <span data-ttu-id="7892b-143">Um GUID correspondente ao cliente.</span><span class="sxs-lookup"><span data-stu-id="7892b-143">A GUID corresponding to the customer.</span></span>             |
| <span data-ttu-id="7892b-144">**id-para-subscrição**</span><span class="sxs-lookup"><span data-stu-id="7892b-144">**id-for-subscription**</span></span> | <span data-ttu-id="7892b-145">**guid**</span><span class="sxs-lookup"><span data-stu-id="7892b-145">**guid**</span></span> | <span data-ttu-id="7892b-146">Y</span><span class="sxs-lookup"><span data-stu-id="7892b-146">Y</span></span>        | <span data-ttu-id="7892b-147">Um GUID correspondente à subscrição inicial.</span><span class="sxs-lookup"><span data-stu-id="7892b-147">A GUID corresponding to the initial subscription.</span></span> |
| <span data-ttu-id="7892b-148">**id-for-target**</span><span class="sxs-lookup"><span data-stu-id="7892b-148">**id-for-target**</span></span>       | <span data-ttu-id="7892b-149">**guid**</span><span class="sxs-lookup"><span data-stu-id="7892b-149">**guid**</span></span> | <span data-ttu-id="7892b-150">Y</span><span class="sxs-lookup"><span data-stu-id="7892b-150">Y</span></span>        | <span data-ttu-id="7892b-151">Um GUID correspondente à subscrição-alvo.</span><span class="sxs-lookup"><span data-stu-id="7892b-151">A GUID corresponding to the target subscription.</span></span>  |

### <a name="request-headers"></a><span data-ttu-id="7892b-152">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="7892b-152">Request headers</span></span>

<span data-ttu-id="7892b-153">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="7892b-153">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="7892b-154">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="7892b-154">Request body</span></span>

<span data-ttu-id="7892b-155">Nenhum</span><span class="sxs-lookup"><span data-stu-id="7892b-155">None</span></span>

### <a name="request-example"></a><span data-ttu-id="7892b-156">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="7892b-156">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription}/upgrades HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 18752a69-1aa1-4ef7-8f9d-eb3681b2d70a
MS-CorrelationId: 81b08ffe-4cf8-49cd-82db-5c2fb0a8e132
X-Locale: en-US

POST https://api.partnercenter.microsoft.com/v1/customers/{customer-tenant-id}/subscriptions/{id-for-target}/upgrades HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 750fd5ea-904b-4c3e-b476-60d0feacab0d
MS-CorrelationId: 81b08ffe-4cf8-49cd-82db-5c2fb0a8e132
X-Locale: en-US
Content-Type: application/json
Content-Length: 1098
Expect: 100-continue

{
    "TargetOffer":{
        "Id":"796B6B5F-613C-4E24-A17C-EBA730D49C02",
        "Name":"Office 365 Enterprise E3",
        "Description":"The best plan for businesses that need full productivity, communication and collaboration tools with the familiar Office suite, including Office Online.",
        "MinimumQuantity":1,
        "MaximumQuantity":10000000,
        "Rank":61,
        "Uri":"/3c95518e-8c37-41e3-9627-0ca339200f53/Offers/796B6B5F-613C-4E24-A17C-EBA730D49C02",
        "Locale":"en-us",
        "Country":"US",
        "Category":{
            "Id":"Enterprise_Key",
            "Name":"Enterprise",
            "Rank":20,
            "Locale":"en-us",
            "Country":"US",
            "Attributes":{
                "ObjectType":"OfferCategory"
            }
        },
        "PrerequisiteOffers":[],
        "IsAddOn":false,
        "IsAvailableForPurchase":true,
        "Billing":"license",
        "IsAutoRenewable":true,
        "Product":{
            "Id":"6fd2c87f-b296-42f0-b197-1e91e994b900",
            "Name":"Office 365 Enterprise E3",
            "Unit":"Licenses"
        },
        "UnitType":"Licenses",
        "Links":{
            "LearnMore":{
                "Uri":"http://g.microsoftonline.com/0BXPS00en/1015",
                "Method":"GET",
                "Headers":[]
            }
        }
        "Attributes":{
            "ObjectType":"Offer"
        }
    },
    "UpgradeType":1,
    "IsEligible":true,
    "Quantity":1,
    "UpgradeErrors":[],
    "Attributes":{
        "ObjectType":"Upgrade"
    }
}
```

## <a name="rest-response"></a><span data-ttu-id="7892b-157">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="7892b-157">REST response</span></span>

<span data-ttu-id="7892b-158">Se for bem sucedido, este método devolve um recurso de resultado **de atualização** no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="7892b-158">If successful, this method returns an **Upgrade** result resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="7892b-159">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="7892b-159">Response success and error codes</span></span>

<span data-ttu-id="7892b-160">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="7892b-160">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="7892b-161">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="7892b-161">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="7892b-162">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="7892b-162">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="7892b-163">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="7892b-163">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 138
Content-Type: application/json
MS-CorrelationId: 81b08ffe-4cf8-49cd-82db-5c2fb0a8e132
MS-RequestId: 18752a69-1aa1-4ef7-8f9d-eb3681b2d70a
Date: Fri, 29 Jan 2016 20:42:26 GMT

{
    "totalCount": 1,
    "items": [{
        "targetOffer": {
            "id": "91FD106F-4B2C-4938-95AC-F54F74E9A239",
            "name": "Office 365 Enterprise E1",
            "description": "For businesses that need communication and collaboration tools and the ability to read and do lightweight editing of documents with Office Online.",
            "minimumQuantity": 1,
            "maximumQuantity": 10000000,
            "rank": 48,
            "uri": "/3c95518e-8c37-41e3-9627-0ca339200f53/Offers/91FD106F-4B2C-4938-95AC-F54F74E9A239",
            "locale": "en-us",
            "country": "US",
            "category": {
                "id": "Enterprise_Key",
                "name": "Enterprise",
                "rank": 20,
                "locale": "en-us",
                "country": "US",
                "attributes": {
                    "objectType": "OfferCategory"
                }
            },
            "prerequisiteOffers": [],
            "isAddOn": false,
            "isAvailableForPurchase": true,
            "billing": "license",
            "isAutoRenewable": true,
            "isInternal": false,
            "conversionTargetOffers": [],
            "partnerQualifications": ["none"],
            "product": {
                "id": "18181a46-0d4e-45cd-891e-60aabd171b4e",
                "name": "Office 365 Enterprise E1",
                "unit": "Licenses"
            },
            "unitType": "Licenses",
            "links": {
                "learnMore": {
                    "uri": "http://g.microsoftonline.com/0BXPS00en/1013",
                    "method": "GET",
                    "headers": []
                },
                "self": {
                    "uri": "/offers/91FD106F-4B2C-4938-95AC-F54F74E9A239?country=US",
                    "method": "GET",
                    "headers": []
                }
            },
            "attributes": {
                "objectType": "Offer"
            }
        },
        "upgradeType": "upgrade_only",
        "isEligible": false,
        "quantity": 1,
        "upgradeErrors": [{
            "code": 2,
            "description": "Subscription cannot be upgraded because the source subscription state is not active.  Additional Details contains the current source subscription state.",
            "attributes": {
                "objectType": "UpgradeError"
            }
        }],
        "attributes": {
            "objectType": "Upgrade"
        }
    }],
    "attributes": {
        "objectType": "Collection"
    }
}

HTTP/1.1 200 OK
Content-Length: 448
Content-Type: application/json
MS-CorrelationId: 81b08ffe-4cf8-49cd-82db-5c2fb0a8e132
MS-RequestId: 750fd5ea-904b-4c3e-b476-60d0feacab0d
MS-CV: RnK86LBbDkWP/w2R.0
MS-ServerId: 102031201
Date: Fri, 29 Jan 2016 20:44:21 GMT

{
    "sourceSubscriptionId":"896a2862-67e2-4f3d-bb3f-c50c42b5fad8",
    "targetSubscriptionId":"2add8a55-454a-4ae5-a4c9-5107dc6e9768",
    "upgradeType":1,
    "upgradeErrors":[],
    "licenseErrors":[],
    "attributes":{
        "objectType":"UpgradeResult"
    }
}
```
