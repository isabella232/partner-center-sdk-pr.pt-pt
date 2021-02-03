---
title: Obter uma lista de produtos (por cliente)
description: Pode utilizar um identificador de clientes para obter uma coleção de produtos por cliente.
ms.assetid: ''
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 98a099c458535123f675c6452db950b087b9f387
ms.sourcegitcommit: d53d300dc7fb01aeb4ef85bf2e3a6b80f868dc57
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/14/2020
ms.locfileid: "97769451"
---
# <a name="get-a-list-of-products-by-customer"></a><span data-ttu-id="25d37-103">Obter uma lista de produtos (por cliente)</span><span class="sxs-lookup"><span data-stu-id="25d37-103">Get a list of products (by customer)</span></span>

<span data-ttu-id="25d37-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="25d37-104">**Applies to:**</span></span>

- <span data-ttu-id="25d37-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="25d37-105">Partner Center</span></span>
- <span data-ttu-id="25d37-106">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="25d37-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="25d37-107">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="25d37-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="25d37-108">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="25d37-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="25d37-109">Pode utilizar os seguintes métodos para obter uma coleção de produtos para um cliente existente.</span><span class="sxs-lookup"><span data-stu-id="25d37-109">You can use the following methods to get a collection of products for an existing customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="25d37-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="25d37-110">Prerequisites</span></span>

- <span data-ttu-id="25d37-111">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="25d37-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="25d37-112">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="25d37-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="25d37-113">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="25d37-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="25d37-114">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="25d37-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="25d37-115">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="25d37-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="25d37-116">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="25d37-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="25d37-117">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="25d37-117">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="25d37-118">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="25d37-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="rest-request"></a><span data-ttu-id="25d37-119">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="25d37-119">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="25d37-120">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="25d37-120">Request syntax</span></span>

| <span data-ttu-id="25d37-121">Método</span><span class="sxs-lookup"><span data-stu-id="25d37-121">Method</span></span> | <span data-ttu-id="25d37-122">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="25d37-122">Request URI</span></span>                                                                                                              |
|--------|--------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="25d37-123">POST</span><span class="sxs-lookup"><span data-stu-id="25d37-123">POST</span></span>   | <span data-ttu-id="25d37-124">[*\{ baseURL \}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/produtos?targetView={targetView} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="25d37-124">[*\{baseURL\}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/products?targetView={targetView} HTTP/1.1</span></span> |

#### <a name="request-uri-parameters"></a><span data-ttu-id="25d37-125">Solicite parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="25d37-125">Request URI parameters</span></span>

| <span data-ttu-id="25d37-126">Nome</span><span class="sxs-lookup"><span data-stu-id="25d37-126">Name</span></span>               | <span data-ttu-id="25d37-127">Tipo</span><span class="sxs-lookup"><span data-stu-id="25d37-127">Type</span></span> | <span data-ttu-id="25d37-128">Necessário</span><span class="sxs-lookup"><span data-stu-id="25d37-128">Required</span></span> | <span data-ttu-id="25d37-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="25d37-129">Description</span></span>                                                                                 |
|--------------------|------|----------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="25d37-130">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="25d37-130">**customer-tenant-id**</span></span> | <span data-ttu-id="25d37-131">GUID</span><span class="sxs-lookup"><span data-stu-id="25d37-131">GUID</span></span> | <span data-ttu-id="25d37-132">Sim</span><span class="sxs-lookup"><span data-stu-id="25d37-132">Yes</span></span> | <span data-ttu-id="25d37-133">O valor é um **cliente-id-inquilino-inquilino-id,** que é um identificador que lhe permite especificar um cliente.</span><span class="sxs-lookup"><span data-stu-id="25d37-133">The value is a GUID-formatted **customer-tenant-id**, which is an identifier that allows you to specify a customer.</span></span> |
| <span data-ttu-id="25d37-134">**targetView**</span><span class="sxs-lookup"><span data-stu-id="25d37-134">**targetView**</span></span> | <span data-ttu-id="25d37-135">string</span><span class="sxs-lookup"><span data-stu-id="25d37-135">string</span></span> | <span data-ttu-id="25d37-136">Sim</span><span class="sxs-lookup"><span data-stu-id="25d37-136">Yes</span></span> | <span data-ttu-id="25d37-137">Identifica a visão do catálogo.</span><span class="sxs-lookup"><span data-stu-id="25d37-137">Identifies the target view of the catalog.</span></span> <span data-ttu-id="25d37-138">Os valores suportados são:</span><span class="sxs-lookup"><span data-stu-id="25d37-138">The supported values are:</span></span> <br/><br/><span data-ttu-id="25d37-139">**Azure,** que inclui todos os itens Azure</span><span class="sxs-lookup"><span data-stu-id="25d37-139">**Azure**, which includes all Azure items</span></span><br/><br/><span data-ttu-id="25d37-140">**AzureReservations**, que inclui todos os itens de reserva Azure</span><span class="sxs-lookup"><span data-stu-id="25d37-140">**AzureReservations**, which includes all Azure reservation items</span></span><br/><br/><span data-ttu-id="25d37-141">**AzureReservationsVM,** que inclui todos os itens de reserva de máquina virtual (VM)</span><span class="sxs-lookup"><span data-stu-id="25d37-141">**AzureReservationsVM**, which includes all virtual machine (VM) reservation items</span></span><br/><br/><span data-ttu-id="25d37-142">**AzureReservationsSQL,** que inclui todos os itens de reserva SQL</span><span class="sxs-lookup"><span data-stu-id="25d37-142">**AzureReservationsSQL**, which includes all SQL reservation items</span></span><br/><br/><span data-ttu-id="25d37-143">**AzureReservationsCosmosDb,** que inclui todos os itens de reserva da base de dados cosmos</span><span class="sxs-lookup"><span data-stu-id="25d37-143">**AzureReservationsCosmosDb**, which includes all Cosmos database reservation items</span></span><br/><br/><span data-ttu-id="25d37-144">**MicrosoftAzure**, que inclui itens para subscrições microsoft Azure **(MS-AZR-0145P**) e planos Azure</span><span class="sxs-lookup"><span data-stu-id="25d37-144">**MicrosoftAzure**, which includes items for Microsoft Azure subscriptions (**MS-AZR-0145P**) and Azure plans</span></span><br/><br/><span data-ttu-id="25d37-145">**OnlineServices**, que inclui todos os itens de serviço on-line, incluindo produtos de marketplace comercial</span><span class="sxs-lookup"><span data-stu-id="25d37-145">**OnlineServices**, which  includes all online service items, including commercial marketplace products</span></span><br/><br/><span data-ttu-id="25d37-146">**Software**, que inclui todos os itens de software</span><span class="sxs-lookup"><span data-stu-id="25d37-146">**Software**, which  includes all software items</span></span><br/><br/><span data-ttu-id="25d37-147">**SoftwareSUSELinux,** que inclui todos os itens SUSE Linux de software</span><span class="sxs-lookup"><span data-stu-id="25d37-147">**SoftwareSUSELinux**, which includes all software SUSE Linux items</span></span><br/><br/><span data-ttu-id="25d37-148">**SoftwarePerpetual,** que inclui todos os itens de software perpétuos</span><span class="sxs-lookup"><span data-stu-id="25d37-148">**SoftwarePerpetual**, which includes all perpetual software items</span></span><br/><br/><span data-ttu-id="25d37-149">**SoftwareSubscriptions**, que inclui todos os itens de subscrição de software</span><span class="sxs-lookup"><span data-stu-id="25d37-149">**SoftwareSubscriptions**, which includes all software subscription items</span></span>  |

### <a name="request-header"></a><span data-ttu-id="25d37-150">Cabeçalho do pedido</span><span class="sxs-lookup"><span data-stu-id="25d37-150">Request header</span></span>

<span data-ttu-id="25d37-151">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="25d37-151">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="25d37-152">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="25d37-152">Request body</span></span>

<span data-ttu-id="25d37-153">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="25d37-153">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="25d37-154">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="25d37-154">Request example</span></span>

<span data-ttu-id="25d37-155">Pedido de uma lista de produtos à base de uso da Azure disponíveis para um determinado cliente.</span><span class="sxs-lookup"><span data-stu-id="25d37-155">Request for a list of Azure usage-based products available to a given customer.</span></span> <span data-ttu-id="25d37-156">Os produtos para os planos Microsoft Azure (MS-AZR-0145P) e Azure serão devolvidos para clientes em nuvem pública:</span><span class="sxs-lookup"><span data-stu-id="25d37-156">Products for both Microsoft Azure (MS-AZR-0145P) and Azure plans will be returned for customers in public cloud:</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/65543400-f8b0-4783-8530-6d35ab8c6801/products?targetView=MicrosoftAzure HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 83643f5e-5dfd-4375-88ed-054412460dc8
MS-CorrelationId: b1939cb2-e83d-4fb0-989f-514fb741b734
```

## <a name="rest-response"></a><span data-ttu-id="25d37-157">Resposta de repouso</span><span class="sxs-lookup"><span data-stu-id="25d37-157">Rest response</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="25d37-158">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="25d37-158">Response success and error codes</span></span>

<span data-ttu-id="25d37-159">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="25d37-159">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="25d37-160">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="25d37-160">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="25d37-161">Para obter a lista completa, consulte os [códigos de erro do Partner Center](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="25d37-161">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

<span data-ttu-id="25d37-162">Este método devolve os seguintes códigos de erro:</span><span class="sxs-lookup"><span data-stu-id="25d37-162">This method returns the following error codes:</span></span>

| <span data-ttu-id="25d37-163">Código de Estado HTTP</span><span class="sxs-lookup"><span data-stu-id="25d37-163">HTTP Status Code</span></span> | <span data-ttu-id="25d37-164">Código de erro</span><span class="sxs-lookup"><span data-stu-id="25d37-164">Error code</span></span>   | <span data-ttu-id="25d37-165">Descrição</span><span class="sxs-lookup"><span data-stu-id="25d37-165">Description</span></span>                     |
|------------------|--------------|---------------------------------|
| <span data-ttu-id="25d37-166">403</span><span class="sxs-lookup"><span data-stu-id="25d37-166">403</span></span> | <span data-ttu-id="25d37-167">400036</span><span class="sxs-lookup"><span data-stu-id="25d37-167">400036</span></span> | <span data-ttu-id="25d37-168">Não é permitido o acesso ao targetView solicitado.</span><span class="sxs-lookup"><span data-stu-id="25d37-168">Access to the requested targetView is not allowed.</span></span> |

### <a name="response-example"></a><span data-ttu-id="25d37-169">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="25d37-169">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1909
Content-Type: application/json; charset=utf-8
MS-CorrelationId: cad955c2-8efc-47fe-b112-548ff002ba18
MS-RequestId: ae7288e2-2673-4ad4-8c12-7aad818d5949

{
    "totalCount": 2,
    "items": [
        {
            "id": "MS-AZR-0145P",
            "productId": "9DEA7946-EC2C-441E-9FFD-E3B275F7E838",
            "title": "Microsoft Azure",
            "description": "Azure Cloud Solution Provider offer for Partner and Resellers",
            "minimumQuantity": 1,
            "maximumQuantity": 1,
            "isTrial": false,
            "supportedBillingCycles": [
                "monthly"
            ],
            "purchasePrerequisites": [
                "MicrosoftCloudAgreement"
            ],
            "actions": [
                "Refund"
            ],
            "dynamicAttributes": {
                "isMicrosoftProduct": true,
                "billingType": "usage",
                "category": "Enterprise",
                "isAddon": false,
                "prerequisiteSkus": [],
                "rank": 1413,
                "hasAddOns": false,
                "isAutoRenewable": false,
                "upgradeTargetOffers": null,
                "conversionTargetOffers": [],
                "unitType": "Usage-based",
                "limitUnitOfMeasure": "None",
                "limit": 0,
                "reselleeQualifications": [],
                "resellerQualifications": []
            },
            "links": {
                "availabilities": {
                    "uri": "/products/9DEA7946-EC2C-441E-9FFD-E3B275F7E838/skus/MS-AZR-0145P/availabilities?country=US&targetSegment=Commercial",
                    "method": "GET",
                    "headers": []
                },
                "self": {
                    "uri": "/products/9DEA7946-EC2C-441E-9FFD-E3B275F7E838/skus/MS-AZR-0145P?country=US",
                    "method": "GET",
                    "headers": []
                }
            }
        },
        {
            "id": "0001",
            "productId": "DZH318Z0BPS6",
            "title": "Microsoft Azure plan",
            "description": "Microsoft Azure plan (MS-AZR-0017G)",
            "minimumQuantity": 1,
            "maximumQuantity": 1,
            "isTrial": false,
            "supportedBillingCycles": [
                "one_time"
            ],
            "purchasePrerequisites": [
                "MicrosoftCustomerAgreement"
            ],
            "inventoryVariables": [],
            "provisioningVariables": [],
            "actions": [
                "Refund"
            ],
            "dynamicAttributes": {
                "isMicrosoftProduct": true,
                "pilotProgram": "modernazurepilot"
            },
            "links": {
                "availabilities": {
                    "uri": "/products/DZH318Z0BPS6/skus/0001/availabilities?country=US&targetSegment=Commercial",
                    "method": "GET",
                    "headers": []
                },
                "self": {
                    "uri": "/products/DZH318Z0BPS6/skus/0001?country=US",
                    "method": "GET",
                    "headers": []
                }
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/customers/e2a0c0f3-0f74-4d1c-808c-dfa511481913/products/all/skus?targetView=MicrosoftAzure&targetSegment=Commercial",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```
