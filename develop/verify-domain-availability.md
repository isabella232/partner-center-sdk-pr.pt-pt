---
title: Verificar a disponibilidade do domínio
description: Como determinar se um domínio está disponível para utilização.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: e2b8f0438516cc0aff9c4d8159c22de43ec582e4
ms.sourcegitcommit: 4275f9f67f9479ce27af6a9fda96fe86d0bc0b44
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/05/2021
ms.locfileid: "111530281"
---
# <a name="verify-domain-availability"></a><span data-ttu-id="e2e2b-103">Verificar a disponibilidade do domínio</span><span class="sxs-lookup"><span data-stu-id="e2e2b-103">Verify domain availability</span></span>

<span data-ttu-id="e2e2b-104">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="e2e2b-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="e2e2b-105">Como determinar se um domínio está disponível para utilização.</span><span class="sxs-lookup"><span data-stu-id="e2e2b-105">How to determine if a domain is available for use.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e2e2b-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="e2e2b-106">Prerequisites</span></span>

- <span data-ttu-id="e2e2b-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="e2e2b-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="e2e2b-108">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="e2e2b-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="e2e2b-109">Um domínio (por `contoso.onmicrosoft.com` exemplo).</span><span class="sxs-lookup"><span data-stu-id="e2e2b-109">A domain (for example `contoso.onmicrosoft.com`).</span></span>

## <a name="c"></a><span data-ttu-id="e2e2b-110">C\#</span><span class="sxs-lookup"><span data-stu-id="e2e2b-110">C\#</span></span>

<span data-ttu-id="e2e2b-111">Para verificar se um domínio está disponível, ligue pela primeira vez [**iAggregatePartner.Domains**](/dotnet/api/microsoft.store.partnercenter.ipartner.domains) para obter uma interface para operações de domínio.</span><span class="sxs-lookup"><span data-stu-id="e2e2b-111">To verify if a domain is available, first call [**IAggregatePartner.Domains**](/dotnet/api/microsoft.store.partnercenter.ipartner.domains) to obtain an interface to domain operations.</span></span> <span data-ttu-id="e2e2b-112">Em seguida, ligue para o método [**ByDomain**](/dotnet/api/microsoft.store.partnercenter.domains.idomaincollection.bydomain) com o domínio para verificar.</span><span class="sxs-lookup"><span data-stu-id="e2e2b-112">Then call the [**ByDomain**](/dotnet/api/microsoft.store.partnercenter.domains.idomaincollection.bydomain) method with the domain to check.</span></span> <span data-ttu-id="e2e2b-113">Este método recupera uma interface para as operações disponíveis para um domínio específico.</span><span class="sxs-lookup"><span data-stu-id="e2e2b-113">This method retrieves an interface to the operations available for a specific domain.</span></span> <span data-ttu-id="e2e2b-114">Finalmente, ligue para o método [**Exista**](/dotnet/api/microsoft.store.partnercenter.domains.idomain.exists) para ver se o domínio já existe.</span><span class="sxs-lookup"><span data-stu-id="e2e2b-114">Finally, call the [**Exists**](/dotnet/api/microsoft.store.partnercenter.domains.idomain.exists) method to see if the domain already exists.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// const string domain = "contoso.onmicrosoft.com";

bool result = partnerOperations.Domains.ByDomain(domain).Exists();
```

<span data-ttu-id="e2e2b-115">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="e2e2b-115">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="e2e2b-116">**Project**: Partner Center SDK Samples **Class**: CheckDomainAvailability.cs</span><span class="sxs-lookup"><span data-stu-id="e2e2b-116">**Project**: Partner Center SDK Samples **Class**: CheckDomainAvailability.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="e2e2b-117">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="e2e2b-117">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="e2e2b-118">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="e2e2b-118">Request syntax</span></span>

| <span data-ttu-id="e2e2b-119">Método</span><span class="sxs-lookup"><span data-stu-id="e2e2b-119">Method</span></span>   | <span data-ttu-id="e2e2b-120">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="e2e2b-120">Request URI</span></span>                                                              |
|----------|--------------------------------------------------------------------------|
| <span data-ttu-id="e2e2b-121">**CABEÇA**</span><span class="sxs-lookup"><span data-stu-id="e2e2b-121">**HEAD**</span></span> | <span data-ttu-id="e2e2b-122">[*{baseURL}*](partner-center-rest-urls.md)/v1/domínios/{domínio} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="e2e2b-122">[*{baseURL}*](partner-center-rest-urls.md)/v1/domains/{domain} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="e2e2b-123">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="e2e2b-123">URI parameter</span></span>

<span data-ttu-id="e2e2b-124">Utilize o seguinte parâmetro de consulta para verificar a disponibilidade de domínio.</span><span class="sxs-lookup"><span data-stu-id="e2e2b-124">Use the following query parameter to verify domain availability.</span></span>

| <span data-ttu-id="e2e2b-125">Nome</span><span class="sxs-lookup"><span data-stu-id="e2e2b-125">Name</span></span>       | <span data-ttu-id="e2e2b-126">Tipo</span><span class="sxs-lookup"><span data-stu-id="e2e2b-126">Type</span></span>       | <span data-ttu-id="e2e2b-127">Necessário</span><span class="sxs-lookup"><span data-stu-id="e2e2b-127">Required</span></span> | <span data-ttu-id="e2e2b-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="e2e2b-128">Description</span></span>                                   |
|------------|------------|----------|-----------------------------------------------|
| <span data-ttu-id="e2e2b-129">**domínio**</span><span class="sxs-lookup"><span data-stu-id="e2e2b-129">**domain**</span></span> | <span data-ttu-id="e2e2b-130">**string**</span><span class="sxs-lookup"><span data-stu-id="e2e2b-130">**string**</span></span> | <span data-ttu-id="e2e2b-131">Y</span><span class="sxs-lookup"><span data-stu-id="e2e2b-131">Y</span></span>        | <span data-ttu-id="e2e2b-132">Uma corda que identifica o domínio para verificar.</span><span class="sxs-lookup"><span data-stu-id="e2e2b-132">A string that identifies the domain to check.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="e2e2b-133">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="e2e2b-133">Request headers</span></span>

<span data-ttu-id="e2e2b-134">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="e2e2b-134">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="e2e2b-135">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="e2e2b-135">Request body</span></span>

<span data-ttu-id="e2e2b-136">Nenhuma</span><span class="sxs-lookup"><span data-stu-id="e2e2b-136">None</span></span>

### <a name="request-example"></a><span data-ttu-id="e2e2b-137">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="e2e2b-137">Request example</span></span>

```http
HEAD https://api.partnercenter.microsoft.com/v1/domains/contoso.onmicrosoft.com HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: cf5b00d6-9240-431c-a973-cc06c904e5bf
MS-CorrelationId: ec57501a-a4c3-45ee-ab2b-da4250545fc9
X-Locale: en-US
Host: api.partnercenter.microsoft.com
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="e2e2b-138">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="e2e2b-138">REST response</span></span>

<span data-ttu-id="e2e2b-139">Se o domínio existir, não está disponível para utilização e é devolvido um código de estado de resposta 200 OK.</span><span class="sxs-lookup"><span data-stu-id="e2e2b-139">If the domain exists, it isn't available for use and a response status code 200 OK is returned.</span></span> <span data-ttu-id="e2e2b-140">Se o domínio não for encontrado, está disponível para utilização e é devolvido um código de estado de resposta 404 Não Encontrado.</span><span class="sxs-lookup"><span data-stu-id="e2e2b-140">If the domain isn't found, it's available for use and a response status code 404 Not Found is returned.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="e2e2b-141">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="e2e2b-141">Response success and error codes</span></span>

<span data-ttu-id="e2e2b-142">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="e2e2b-142">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="e2e2b-143">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="e2e2b-143">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="e2e2b-144">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="e2e2b-144">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example-for-when-the-domain-is-already-in-use"></a><span data-ttu-id="e2e2b-145">Exemplo de resposta para quando o domínio já está em uso</span><span class="sxs-lookup"><span data-stu-id="e2e2b-145">Response example for when the domain is already in use</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 0
MS-CorrelationId: ec57501a-a4c3-45ee-ab2b-da4250545fc9
MS-RequestId: cf5b00d6-9240-431c-a973-cc06c904e5bf
MS-CV: 7UXAHds8J0mNUCSp.0
MS-ServerId: 201022015
Date: Tue, 31 Jan 2017 22:22:35 GMT
```

### <a name="response-example-for-when-the-domain-is-available"></a><span data-ttu-id="e2e2b-146">Exemplo de resposta para quando o domínio está disponível</span><span class="sxs-lookup"><span data-stu-id="e2e2b-146">Response example for when the domain is available</span></span>

```http
HTTP/1.1 404 Not Found
Content-Length: 0
MS-CorrelationId: 54770745-17f0-433c-bd7b-0265e5b38f98
MS-RequestId: 1169a4cd-3be7-4e29-9cb3-0f78ffa2e91e
MS-CV: RRmc+bEw9U2e97CC.0
MS-ServerId: 202010406
Date: Tue, 31 Jan 2017 22:36:01 GMT
```
