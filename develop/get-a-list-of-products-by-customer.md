---
title: Obter uma lista de produtos (por cliente)
description: Pode utilizar um identificador de clientes para obter uma coleção de produtos por cliente.
ms.assetid: ''
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: a7cb2430aa93beb89e4d1f9b8c89a016d66624ca
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874198"
---
# <a name="get-a-list-of-products-by-customer"></a><span data-ttu-id="e40c9-103">Obter uma lista de produtos (por cliente)</span><span class="sxs-lookup"><span data-stu-id="e40c9-103">Get a list of products (by customer)</span></span>

<span data-ttu-id="e40c9-104">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="e40c9-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="e40c9-105">Pode utilizar os seguintes métodos para obter uma coleção de produtos para um cliente existente.</span><span class="sxs-lookup"><span data-stu-id="e40c9-105">You can use the following methods to get a collection of products for an existing customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e40c9-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="e40c9-106">Prerequisites</span></span>

- <span data-ttu-id="e40c9-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="e40c9-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="e40c9-108">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="e40c9-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="e40c9-109">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="e40c9-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="e40c9-110">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="e40c9-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="e40c9-111">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="e40c9-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="e40c9-112">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="e40c9-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="e40c9-113">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="e40c9-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="e40c9-114">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="e40c9-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="rest-request"></a><span data-ttu-id="e40c9-115">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="e40c9-115">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="e40c9-116">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="e40c9-116">Request syntax</span></span>

| <span data-ttu-id="e40c9-117">Método</span><span class="sxs-lookup"><span data-stu-id="e40c9-117">Method</span></span> | <span data-ttu-id="e40c9-118">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="e40c9-118">Request URI</span></span>                                                                                                              |
|--------|--------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="e40c9-119">POST</span><span class="sxs-lookup"><span data-stu-id="e40c9-119">POST</span></span>   | <span data-ttu-id="e40c9-120">[*\{ baseURL \}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id}/produtos?targetView={targetView} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="e40c9-120">[*\{baseURL\}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/products?targetView={targetView} HTTP/1.1</span></span> |

#### <a name="request-uri-parameters"></a><span data-ttu-id="e40c9-121">Solicite parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="e40c9-121">Request URI parameters</span></span>

| <span data-ttu-id="e40c9-122">Nome</span><span class="sxs-lookup"><span data-stu-id="e40c9-122">Name</span></span>               | <span data-ttu-id="e40c9-123">Tipo</span><span class="sxs-lookup"><span data-stu-id="e40c9-123">Type</span></span> | <span data-ttu-id="e40c9-124">Necessário</span><span class="sxs-lookup"><span data-stu-id="e40c9-124">Required</span></span> | <span data-ttu-id="e40c9-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="e40c9-125">Description</span></span>                                                                                 |
|--------------------|------|----------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="e40c9-126">**cliente-inquilino-id**</span><span class="sxs-lookup"><span data-stu-id="e40c9-126">**customer-tenant-id**</span></span> | <span data-ttu-id="e40c9-127">GUID</span><span class="sxs-lookup"><span data-stu-id="e40c9-127">GUID</span></span> | <span data-ttu-id="e40c9-128">Yes</span><span class="sxs-lookup"><span data-stu-id="e40c9-128">Yes</span></span> | <span data-ttu-id="e40c9-129">O valor é um **cliente-id-inquilino-inquilino-id,** que é um identificador que lhe permite especificar um cliente.</span><span class="sxs-lookup"><span data-stu-id="e40c9-129">The value is a GUID-formatted **customer-tenant-id**, which is an identifier that allows you to specify a customer.</span></span> |
| <span data-ttu-id="e40c9-130">**targetView**</span><span class="sxs-lookup"><span data-stu-id="e40c9-130">**targetView**</span></span> | <span data-ttu-id="e40c9-131">string</span><span class="sxs-lookup"><span data-stu-id="e40c9-131">string</span></span> | <span data-ttu-id="e40c9-132">Yes</span><span class="sxs-lookup"><span data-stu-id="e40c9-132">Yes</span></span> | <span data-ttu-id="e40c9-133">Identifica a visão do catálogo.</span><span class="sxs-lookup"><span data-stu-id="e40c9-133">Identifies the target view of the catalog.</span></span> <span data-ttu-id="e40c9-134">Os valores suportados são:</span><span class="sxs-lookup"><span data-stu-id="e40c9-134">The supported values are:</span></span> <br/><br/><span data-ttu-id="e40c9-135">**Azure,** que inclui todos os itens Azure</span><span class="sxs-lookup"><span data-stu-id="e40c9-135">**Azure**, which includes all Azure items</span></span><br/><br/><span data-ttu-id="e40c9-136">**AzureReservations**, que inclui todos os itens de reserva Azure</span><span class="sxs-lookup"><span data-stu-id="e40c9-136">**AzureReservations**, which includes all Azure reservation items</span></span><br/><br/><span data-ttu-id="e40c9-137">**AzureReservationsVM,** que inclui todos os itens de reserva de máquina virtual (VM)</span><span class="sxs-lookup"><span data-stu-id="e40c9-137">**AzureReservationsVM**, which includes all virtual machine (VM) reservation items</span></span><br/><br/><span data-ttu-id="e40c9-138">**AzureReservationsSQL,** que inclui todos os itens de reserva SQL</span><span class="sxs-lookup"><span data-stu-id="e40c9-138">**AzureReservationsSQL**, which includes all SQL reservation items</span></span><br/><br/><span data-ttu-id="e40c9-139">**AzureReservationsCosmosDb,** que inclui todos os itens de reserva da base de dados cosmos</span><span class="sxs-lookup"><span data-stu-id="e40c9-139">**AzureReservationsCosmosDb**, which includes all Cosmos database reservation items</span></span><br/><br/><span data-ttu-id="e40c9-140">**MicrosoftAzure**, que inclui itens para subscrições Microsoft Azure **(MS-AZR-0145P)** e planos Azure</span><span class="sxs-lookup"><span data-stu-id="e40c9-140">**MicrosoftAzure**, which includes items for Microsoft Azure subscriptions (**MS-AZR-0145P**) and Azure plans</span></span><br/><br/><span data-ttu-id="e40c9-141">**OnlineServices**, que inclui todos os itens de serviço on-line, incluindo produtos de marketplace comercial</span><span class="sxs-lookup"><span data-stu-id="e40c9-141">**OnlineServices**, which includes all online service items, including commercial marketplace products</span></span><br/><br/><span data-ttu-id="e40c9-142">**Software**, que inclui todos os itens de software</span><span class="sxs-lookup"><span data-stu-id="e40c9-142">**Software**, which  includes all software items</span></span><br/><br/><span data-ttu-id="e40c9-143">**SoftwareSUSELinux,** que inclui todos os itens SUSE Linux de software</span><span class="sxs-lookup"><span data-stu-id="e40c9-143">**SoftwareSUSELinux**, which includes all software SUSE Linux items</span></span><br/><br/><span data-ttu-id="e40c9-144">**SoftwarePerpetual,** que inclui todos os itens de software perpétuos</span><span class="sxs-lookup"><span data-stu-id="e40c9-144">**SoftwarePerpetual**, which includes all perpetual software items</span></span><br/><br/><span data-ttu-id="e40c9-145">**SoftwareSubscriptions**, que inclui todos os itens de subscrição de software</span><span class="sxs-lookup"><span data-stu-id="e40c9-145">**SoftwareSubscriptions**, which includes all software subscription items</span></span>  |

### <a name="request-header"></a><span data-ttu-id="e40c9-146">Cabeçalho do pedido</span><span class="sxs-lookup"><span data-stu-id="e40c9-146">Request header</span></span>

<span data-ttu-id="e40c9-147">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="e40c9-147">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="e40c9-148">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="e40c9-148">Request body</span></span>

<span data-ttu-id="e40c9-149">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="e40c9-149">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="e40c9-150">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="e40c9-150">Request example</span></span>

<span data-ttu-id="e40c9-151">Pedido de uma lista de produtos à base de uso da Azure disponíveis para um determinado cliente.</span><span class="sxs-lookup"><span data-stu-id="e40c9-151">Request for a list of Azure usage-based products available to a given customer.</span></span> <span data-ttu-id="e40c9-152">Os produtos para Microsoft Azure (MS-AZR-0145P) e planos Azure serão devolvidos para clientes em nuvem pública:</span><span class="sxs-lookup"><span data-stu-id="e40c9-152">Products for both Microsoft Azure (MS-AZR-0145P) and Azure plans will be returned for customers in public cloud:</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/65543400-f8b0-4783-8530-6d35ab8c6801/products?targetView=MicrosoftAzure HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 83643f5e-5dfd-4375-88ed-054412460dc8
MS-CorrelationId: b1939cb2-e83d-4fb0-989f-514fb741b734
```

## <a name="rest-response"></a><span data-ttu-id="e40c9-153">Resposta de repouso</span><span class="sxs-lookup"><span data-stu-id="e40c9-153">Rest response</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="e40c9-154">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="e40c9-154">Response success and error codes</span></span>

<span data-ttu-id="e40c9-155">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="e40c9-155">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="e40c9-156">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="e40c9-156">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="e40c9-157">Para obter a lista completa, consulte os [códigos de erro do Partner Center](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="e40c9-157">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

<span data-ttu-id="e40c9-158">Este método devolve os seguintes códigos de erro:</span><span class="sxs-lookup"><span data-stu-id="e40c9-158">This method returns the following error codes:</span></span>

| <span data-ttu-id="e40c9-159">Código de Estado HTTP</span><span class="sxs-lookup"><span data-stu-id="e40c9-159">HTTP Status Code</span></span> | <span data-ttu-id="e40c9-160">Código de erro</span><span class="sxs-lookup"><span data-stu-id="e40c9-160">Error code</span></span>   | <span data-ttu-id="e40c9-161">Description</span><span class="sxs-lookup"><span data-stu-id="e40c9-161">Description</span></span>                     |
|------------------|--------------|---------------------------------|
| <span data-ttu-id="e40c9-162">403</span><span class="sxs-lookup"><span data-stu-id="e40c9-162">403</span></span> | <span data-ttu-id="e40c9-163">400036</span><span class="sxs-lookup"><span data-stu-id="e40c9-163">400036</span></span> | <span data-ttu-id="e40c9-164">Não é permitido o acesso ao targetView solicitado.</span><span class="sxs-lookup"><span data-stu-id="e40c9-164">Access to the requested targetView is not allowed.</span></span> |

### <a name="response-example"></a><span data-ttu-id="e40c9-165">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="e40c9-165">Response example</span></span>

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
