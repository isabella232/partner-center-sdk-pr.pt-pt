---
title: Eliminar um dispositivo para o cliente especificado
description: Como eliminar um dispositivo que pertence a um cliente especificado.
ms.date: 06/20/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 69b5440f2cf07d3cb4ecd5addf429acd64530257
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/22/2020
ms.locfileid: "97769386"
---
# <a name="delete-a-device-for-the-specified-customer"></a><span data-ttu-id="21713-103">Eliminar um dispositivo para o cliente especificado</span><span class="sxs-lookup"><span data-stu-id="21713-103">Delete a device for the specified customer</span></span>

<span data-ttu-id="21713-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="21713-104">**Applies to:**</span></span>

- <span data-ttu-id="21713-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="21713-105">Partner Center</span></span>
- <span data-ttu-id="21713-106">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="21713-106">Partner Center for Microsoft Cloud Germany</span></span>

<span data-ttu-id="21713-107">Este artigo explica como eliminar um dispositivo que pertence a um cliente especificado.</span><span class="sxs-lookup"><span data-stu-id="21713-107">This article explains how to delete a device that belongs to a specified customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="21713-108">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="21713-108">Prerequisites</span></span>

- <span data-ttu-id="21713-109">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="21713-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="21713-110">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="21713-110">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="21713-111">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="21713-111">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="21713-112">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="21713-112">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="21713-113">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="21713-113">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="21713-114">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="21713-114">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="21713-115">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="21713-115">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="21713-116">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="21713-116">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="21713-117">O identificador do lote do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="21713-117">The device batch identifier.</span></span>

- <span data-ttu-id="21713-118">O identificador do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="21713-118">The device identifier.</span></span>

## <a name="c"></a><span data-ttu-id="21713-119">C\#</span><span class="sxs-lookup"><span data-stu-id="21713-119">C\#</span></span>

<span data-ttu-id="21713-120">Para eliminar um dispositivo para o cliente especificado:</span><span class="sxs-lookup"><span data-stu-id="21713-120">To delete a device for the specified customer:</span></span>

1. <span data-ttu-id="21713-121">Ligue para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o identificador de clientes para recuperar uma interface para operações no cliente.</span><span class="sxs-lookup"><span data-stu-id="21713-121">Call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer identifier to retrieve an interface to operations on the customer.</span></span>

2. <span data-ttu-id="21713-122">Ligue para o método [**DeviceBatches.ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatchcollection.byid) com o identificador de lote do dispositivo para obter uma interface para as operações do lote especificado.</span><span class="sxs-lookup"><span data-stu-id="21713-122">Call the [**DeviceBatches.ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatchcollection.byid) method with the device batch identifier to get an interface to operations for the specified batch.</span></span>

3. <span data-ttu-id="21713-123">Ligue para o método [**Dispositivos.ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicecollection.byid) para obter uma interface para funcionar no dispositivo especificado.</span><span class="sxs-lookup"><span data-stu-id="21713-123">Call the [**Devices.ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicecollection.byid) method to get an interface to operation on the specified device.</span></span>

4. <span data-ttu-id="21713-124">Ligue para o método [**Eliminar**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevice.delete) ou [**EliminarAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevice.deleteasync) para eliminar o dispositivo do lote.</span><span class="sxs-lookup"><span data-stu-id="21713-124">Call the [**Delete**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevice.delete) or [**DeleteAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevice.deleteasync) method to delete the device from the batch.</span></span>

``` csharp
IAggregatePartner partnerOperations;
string selectedCustomerId;
string selectedDeviceBatchId;
string selectedDeviceId;

partnerOperations.Customers.ById(selectedCustomerId).DeviceBatches.ById(selectedDeviceBatchId).Devices.ById(selectedDeviceId).Delete();
```

<span data-ttu-id="21713-125">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="21713-125">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="21713-126">**Projeto**: Partner Center SDK Samples **Class**: DeleteDevice.cs</span><span class="sxs-lookup"><span data-stu-id="21713-126">**Project**: Partner Center SDK Samples **Class**: DeleteDevice.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="21713-127">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="21713-127">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="21713-128">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="21713-128">Request syntax</span></span>

| <span data-ttu-id="21713-129">Método</span><span class="sxs-lookup"><span data-stu-id="21713-129">Method</span></span>     | <span data-ttu-id="21713-130">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="21713-130">Request URI</span></span>                                                                                                                        |
|------------|------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="21713-131">DELETE</span><span class="sxs-lookup"><span data-stu-id="21713-131">DELETE</span></span>     | <span data-ttu-id="21713-132">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/deviceBatches/{devicebatch-id}/devices/{device-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="21713-132">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/deviceBatches/{devicebatch-id}/devices/{device-id} HTTP/1.1</span></span>  |

#### <a name="uri-parameters"></a><span data-ttu-id="21713-133">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="21713-133">URI parameters</span></span>

<span data-ttu-id="21713-134">Utilize os seguintes parâmetros de trajetória ao criar o pedido.</span><span class="sxs-lookup"><span data-stu-id="21713-134">Use the following path parameters when creating the request.</span></span>

| <span data-ttu-id="21713-135">Nome</span><span class="sxs-lookup"><span data-stu-id="21713-135">Name</span></span>           | <span data-ttu-id="21713-136">Tipo</span><span class="sxs-lookup"><span data-stu-id="21713-136">Type</span></span>   | <span data-ttu-id="21713-137">Necessário</span><span class="sxs-lookup"><span data-stu-id="21713-137">Required</span></span> | <span data-ttu-id="21713-138">Descrição</span><span class="sxs-lookup"><span data-stu-id="21713-138">Description</span></span>                                                        |
|----------------|--------|----------|--------------------------------------------------------------------|
| <span data-ttu-id="21713-139">id cliente</span><span class="sxs-lookup"><span data-stu-id="21713-139">customer-id</span></span>    | <span data-ttu-id="21713-140">string</span><span class="sxs-lookup"><span data-stu-id="21713-140">string</span></span> | <span data-ttu-id="21713-141">Sim</span><span class="sxs-lookup"><span data-stu-id="21713-141">Yes</span></span>      | <span data-ttu-id="21713-142">Uma cadeia formatada pelo GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="21713-142">A GUID-formatted string that identifies the customer.</span></span>              |
| <span data-ttu-id="21713-143">devicebatch-id</span><span class="sxs-lookup"><span data-stu-id="21713-143">devicebatch-id</span></span> | <span data-ttu-id="21713-144">string</span><span class="sxs-lookup"><span data-stu-id="21713-144">string</span></span> | <span data-ttu-id="21713-145">Sim</span><span class="sxs-lookup"><span data-stu-id="21713-145">Yes</span></span>      | <span data-ttu-id="21713-146">O identificador de lote do dispositivo que contém o dispositivo.</span><span class="sxs-lookup"><span data-stu-id="21713-146">The device batch identifier of the batch that contains the device.</span></span> |
| <span data-ttu-id="21713-147">dispositivo id</span><span class="sxs-lookup"><span data-stu-id="21713-147">device-id</span></span>      | <span data-ttu-id="21713-148">string</span><span class="sxs-lookup"><span data-stu-id="21713-148">string</span></span> | <span data-ttu-id="21713-149">Sim</span><span class="sxs-lookup"><span data-stu-id="21713-149">Yes</span></span>      | <span data-ttu-id="21713-150">O identificador do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="21713-150">The device identifier.</span></span>                                             |

### <a name="request-headers"></a><span data-ttu-id="21713-151">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="21713-151">Request headers</span></span>

<span data-ttu-id="21713-152">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="21713-152">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="21713-153">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="21713-153">Request body</span></span>

<span data-ttu-id="21713-154">Nenhum</span><span class="sxs-lookup"><span data-stu-id="21713-154">None</span></span>

### <a name="request-example"></a><span data-ttu-id="21713-155">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="21713-155">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="21713-156">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="21713-156">REST response</span></span>

<span data-ttu-id="21713-157">Se for bem sucedida, a resposta devolve um código de estado **204 No Content.**</span><span class="sxs-lookup"><span data-stu-id="21713-157">If successful, the response returns a **204 No Content** status code.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="21713-158">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="21713-158">Response success and error codes</span></span>

<span data-ttu-id="21713-159">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="21713-159">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="21713-160">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="21713-160">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="21713-161">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="21713-161">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="21713-162">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="21713-162">Response example</span></span>

```http
HTTP/1.1 204 No Content
Content-Length: 0
MS-CorrelationId: 394d96d0-05b2-4b02-b907-0697632ee3bb
MS-RequestId: 8b3e6f78-220b-4177-861b-33d6f38f7b97
MS-CV: YrLe3w6BbUSMt1fi.0
MS-ServerId: 030020344
Date: Tue, 25 Jul 2017 17:58:53 GMT
```
