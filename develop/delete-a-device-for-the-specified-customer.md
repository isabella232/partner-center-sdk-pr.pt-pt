---
title: Eliminar um dispositivo para o cliente especificado
description: Como eliminar um dispositivo que pertence a um cliente especificado.
ms.date: 06/20/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: a1e05ceb8615d6f84c1df101c542342f9a6eb04b
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973082"
---
# <a name="delete-a-device-for-the-specified-customer"></a><span data-ttu-id="92031-103">Eliminar um dispositivo para o cliente especificado</span><span class="sxs-lookup"><span data-stu-id="92031-103">Delete a device for the specified customer</span></span>

<span data-ttu-id="92031-104">**Aplica-se a**: Partner Center | Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="92031-104">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany</span></span>

<span data-ttu-id="92031-105">Este artigo explica como eliminar um dispositivo que pertence a um cliente especificado.</span><span class="sxs-lookup"><span data-stu-id="92031-105">This article explains how to delete a device that belongs to a specified customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="92031-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="92031-106">Prerequisites</span></span>

- <span data-ttu-id="92031-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="92031-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="92031-108">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="92031-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="92031-109">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="92031-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="92031-110">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="92031-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="92031-111">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="92031-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="92031-112">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="92031-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="92031-113">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="92031-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="92031-114">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="92031-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="92031-115">O identificador do lote do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="92031-115">The device batch identifier.</span></span>

- <span data-ttu-id="92031-116">O identificador do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="92031-116">The device identifier.</span></span>

## <a name="c"></a><span data-ttu-id="92031-117">C\#</span><span class="sxs-lookup"><span data-stu-id="92031-117">C\#</span></span>

<span data-ttu-id="92031-118">Para eliminar um dispositivo para o cliente especificado:</span><span class="sxs-lookup"><span data-stu-id="92031-118">To delete a device for the specified customer:</span></span>

1. <span data-ttu-id="92031-119">Ligue para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o identificador de clientes para recuperar uma interface para operações no cliente.</span><span class="sxs-lookup"><span data-stu-id="92031-119">Call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer identifier to retrieve an interface to operations on the customer.</span></span>

2. <span data-ttu-id="92031-120">Ligue para o método [**DeviceBatches.ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatchcollection.byid) com o identificador de lote do dispositivo para obter uma interface para as operações do lote especificado.</span><span class="sxs-lookup"><span data-stu-id="92031-120">Call the [**DeviceBatches.ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatchcollection.byid) method with the device batch identifier to get an interface to operations for the specified batch.</span></span>

3. <span data-ttu-id="92031-121">Ligue para o método [**Dispositivos.ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicecollection.byid) para obter uma interface para funcionar no dispositivo especificado.</span><span class="sxs-lookup"><span data-stu-id="92031-121">Call the [**Devices.ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicecollection.byid) method to get an interface to operation on the specified device.</span></span>

4. <span data-ttu-id="92031-122">Ligue para o método [**Eliminar**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevice.delete) ou [**EliminarAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevice.deleteasync) para eliminar o dispositivo do lote.</span><span class="sxs-lookup"><span data-stu-id="92031-122">Call the [**Delete**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevice.delete) or [**DeleteAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevice.deleteasync) method to delete the device from the batch.</span></span>

``` csharp
IAggregatePartner partnerOperations;
string selectedCustomerId;
string selectedDeviceBatchId;
string selectedDeviceId;

partnerOperations.Customers.ById(selectedCustomerId).DeviceBatches.ById(selectedDeviceBatchId).Devices.ById(selectedDeviceId).Delete();
```

<span data-ttu-id="92031-123">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="92031-123">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="92031-124">**Project**: Partner Center SDK Samples **Class**: DeleteDevice.cs</span><span class="sxs-lookup"><span data-stu-id="92031-124">**Project**: Partner Center SDK Samples **Class**: DeleteDevice.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="92031-125">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="92031-125">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="92031-126">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="92031-126">Request syntax</span></span>

| <span data-ttu-id="92031-127">Método</span><span class="sxs-lookup"><span data-stu-id="92031-127">Method</span></span>     | <span data-ttu-id="92031-128">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="92031-128">Request URI</span></span>                                                                                                                        |
|------------|------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="92031-129">DELETE</span><span class="sxs-lookup"><span data-stu-id="92031-129">DELETE</span></span>     | <span data-ttu-id="92031-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/deviceBatches/{devicebatch-id}/devices/{device-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="92031-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/deviceBatches/{devicebatch-id}/devices/{device-id} HTTP/1.1</span></span>  |

#### <a name="uri-parameters"></a><span data-ttu-id="92031-131">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="92031-131">URI parameters</span></span>

<span data-ttu-id="92031-132">Utilize os seguintes parâmetros de trajetória ao criar o pedido.</span><span class="sxs-lookup"><span data-stu-id="92031-132">Use the following path parameters when creating the request.</span></span>

| <span data-ttu-id="92031-133">Nome</span><span class="sxs-lookup"><span data-stu-id="92031-133">Name</span></span>           | <span data-ttu-id="92031-134">Tipo</span><span class="sxs-lookup"><span data-stu-id="92031-134">Type</span></span>   | <span data-ttu-id="92031-135">Necessário</span><span class="sxs-lookup"><span data-stu-id="92031-135">Required</span></span> | <span data-ttu-id="92031-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="92031-136">Description</span></span>                                                        |
|----------------|--------|----------|--------------------------------------------------------------------|
| <span data-ttu-id="92031-137">id cliente</span><span class="sxs-lookup"><span data-stu-id="92031-137">customer-id</span></span>    | <span data-ttu-id="92031-138">string</span><span class="sxs-lookup"><span data-stu-id="92031-138">string</span></span> | <span data-ttu-id="92031-139">Yes</span><span class="sxs-lookup"><span data-stu-id="92031-139">Yes</span></span>      | <span data-ttu-id="92031-140">Uma cadeia formatada pelo GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="92031-140">A GUID-formatted string that identifies the customer.</span></span>              |
| <span data-ttu-id="92031-141">devicebatch-id</span><span class="sxs-lookup"><span data-stu-id="92031-141">devicebatch-id</span></span> | <span data-ttu-id="92031-142">string</span><span class="sxs-lookup"><span data-stu-id="92031-142">string</span></span> | <span data-ttu-id="92031-143">Yes</span><span class="sxs-lookup"><span data-stu-id="92031-143">Yes</span></span>      | <span data-ttu-id="92031-144">O identificador de lote do dispositivo que contém o dispositivo.</span><span class="sxs-lookup"><span data-stu-id="92031-144">The device batch identifier of the batch that contains the device.</span></span> |
| <span data-ttu-id="92031-145">dispositivo id</span><span class="sxs-lookup"><span data-stu-id="92031-145">device-id</span></span>      | <span data-ttu-id="92031-146">string</span><span class="sxs-lookup"><span data-stu-id="92031-146">string</span></span> | <span data-ttu-id="92031-147">Yes</span><span class="sxs-lookup"><span data-stu-id="92031-147">Yes</span></span>      | <span data-ttu-id="92031-148">O identificador do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="92031-148">The device identifier.</span></span>                                             |

### <a name="request-headers"></a><span data-ttu-id="92031-149">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="92031-149">Request headers</span></span>

<span data-ttu-id="92031-150">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="92031-150">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="92031-151">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="92031-151">Request body</span></span>

<span data-ttu-id="92031-152">Nenhuma</span><span class="sxs-lookup"><span data-stu-id="92031-152">None</span></span>

### <a name="request-example"></a><span data-ttu-id="92031-153">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="92031-153">Request example</span></span>

```http
DELETE https://api.partnercenter.microsoft.com/v1/customers/47021739-3426-40bf-9601-61b4b6d7c793/deviceBatches/testbatch/devices/7b11cd8b-dd1e-4840-8c4a-84215e4de782 HTTP/1.1
Authorization: Bearer <token>
MS-RequestId: e88d014d-ab70-41de-90a0-f7fd1797267d
MS-CorrelationId: de894e18-f027-4ac0-8b5a-34f0c222af0c
X-Locale: en-US
Content-Length: 0
Content-Type: application/json
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="92031-154">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="92031-154">REST response</span></span>

<span data-ttu-id="92031-155">Se for bem sucedida, a resposta devolve um código de estado **204 No Content.**</span><span class="sxs-lookup"><span data-stu-id="92031-155">If successful, the response returns a **204 No Content** status code.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="92031-156">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="92031-156">Response success and error codes</span></span>

<span data-ttu-id="92031-157">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="92031-157">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="92031-158">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="92031-158">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="92031-159">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="92031-159">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="92031-160">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="92031-160">Response example</span></span>

```http
HTTP/1.1 204 No Content
Content-Length: 0
MS-CorrelationId: 394d96d0-05b2-4b02-b907-0697632ee3bb
MS-RequestId: 8b3e6f78-220b-4177-861b-33d6f38f7b97
MS-CV: YrLe3w6BbUSMt1fi.0
MS-ServerId: 030020344
Date: Tue, 25 Jul 2017 17:58:53 GMT
```
