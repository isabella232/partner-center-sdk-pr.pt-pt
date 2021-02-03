---
title: Obter uma lista de dispositivos para o lote e cliente especificados
description: Como recuperar uma recolha de dispositivos e detalhes do dispositivo no lote de dispositivo especificado para um cliente.
ms.date: 07/25/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 36fe3b97612adfd26c1b498f31b90f743bf774cb
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/19/2020
ms.locfileid: "97769548"
---
# <a name="get-a-list-of-devices-for-the-specified-batch-and-customer"></a><span data-ttu-id="a26b8-103">Obter uma lista de dispositivos para o lote e cliente especificados</span><span class="sxs-lookup"><span data-stu-id="a26b8-103">Get a list of devices for the specified batch and customer</span></span>

<span data-ttu-id="a26b8-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="a26b8-104">**Applies to:**</span></span>

- <span data-ttu-id="a26b8-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="a26b8-105">Partner Center</span></span>
- <span data-ttu-id="a26b8-106">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="a26b8-106">Partner Center for Microsoft Cloud Germany</span></span>

<span data-ttu-id="a26b8-107">Este artigo descreve como recuperar uma coleção de dispositivos num lote de dispositivo especificado para um cliente especificado.</span><span class="sxs-lookup"><span data-stu-id="a26b8-107">This article describes how to retrieve a collection of devices in a specified device batch for a specified customer.</span></span> <span data-ttu-id="a26b8-108">Cada recurso do dispositivo contém detalhes sobre o dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a26b8-108">Each device resource contains details about the device.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a26b8-109">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="a26b8-109">Prerequisites</span></span>

- <span data-ttu-id="a26b8-110">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="a26b8-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="a26b8-111">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="a26b8-111">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="a26b8-112">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="a26b8-112">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="a26b8-113">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="a26b8-113">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="a26b8-114">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="a26b8-114">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="a26b8-115">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="a26b8-115">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="a26b8-116">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="a26b8-116">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="a26b8-117">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="a26b8-117">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="a26b8-118">Um identificador de lote de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a26b8-118">A device batch identifier.</span></span>

## <a name="c"></a><span data-ttu-id="a26b8-119">C\#</span><span class="sxs-lookup"><span data-stu-id="a26b8-119">C\#</span></span>

<span data-ttu-id="a26b8-120">Para recuperar uma coleção dos dispositivos num lote de dispositivo especificado para o cliente especificado:</span><span class="sxs-lookup"><span data-stu-id="a26b8-120">To retrieve a collection of the devices in a specified device batch for the specified customer:</span></span>

1. <span data-ttu-id="a26b8-121">Ligue para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para recuperar uma interface para operações no cliente especificado.</span><span class="sxs-lookup"><span data-stu-id="a26b8-121">Call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to retrieve an interface to operations on the specified customer.</span></span>

2. <span data-ttu-id="a26b8-122">Ligue para o método [**DeviceBatches.ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatchcollection.byid) para obter uma interface para o dispositivo operações de recolha de lotes para o lote especificado.</span><span class="sxs-lookup"><span data-stu-id="a26b8-122">Call the [**DeviceBatches.ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatchcollection.byid) method to get an interface to device batch collection operations for the specified batch.</span></span>

3. <span data-ttu-id="a26b8-123">Recupere a propriedade [**devices**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatch.devices) para obter uma interface para as operações de recolha do dispositivo para o lote.</span><span class="sxs-lookup"><span data-stu-id="a26b8-123">Retrieve the [**Devices**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatch.devices) property to get an interface to device collection operations for the batch.</span></span>

4. <span data-ttu-id="a26b8-124">Ligue para o método [**Get**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicecollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicecollection.getasync) para recuperar a recolha de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="a26b8-124">Call the [**Get**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicecollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicecollection.getasync) method to retrieve the collection of devices.</span></span>

``` csharp
IAggregatePartner partnerOperations;
string selectedCustomerId;
string selectedDeviceBatchId;

var devices =
    partnerOperations.Customers.ById(selectedCustomerId).DeviceBatches.ById(selectedDeviceBatchId).Devices.Get();
```

<span data-ttu-id="a26b8-125">Por exemplo, consulte o seguinte:</span><span class="sxs-lookup"><span data-stu-id="a26b8-125">For an example, see the following:</span></span>

- <span data-ttu-id="a26b8-126">Amostra: [App de teste de consola](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="a26b8-126">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="a26b8-127">Projeto: **Partner Center SDK Samples**</span><span class="sxs-lookup"><span data-stu-id="a26b8-127">Project: **Partner Center SDK Samples**</span></span>
- <span data-ttu-id="a26b8-128">Classe: **GetDevices.cs**</span><span class="sxs-lookup"><span data-stu-id="a26b8-128">Class: **GetDevices.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="a26b8-129">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="a26b8-129">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="a26b8-130">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="a26b8-130">Request syntax</span></span>

| <span data-ttu-id="a26b8-131">Método</span><span class="sxs-lookup"><span data-stu-id="a26b8-131">Method</span></span>  | <span data-ttu-id="a26b8-132">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="a26b8-132">Request URI</span></span>                                                                                                            |
|---------|------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="a26b8-133">**Obter**</span><span class="sxs-lookup"><span data-stu-id="a26b8-133">**GET**</span></span> | <span data-ttu-id="a26b8-134">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{customer-id}/deviceBatches/{devicebatch-id}/dispositivos HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="a26b8-134">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/deviceBatches/{devicebatch-id}/devices HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="a26b8-135">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="a26b8-135">URI parameters</span></span>

<span data-ttu-id="a26b8-136">Utilize os seguintes parâmetros de trajetória ao criar o pedido.</span><span class="sxs-lookup"><span data-stu-id="a26b8-136">Use the following path parameters when creating the request.</span></span>

| <span data-ttu-id="a26b8-137">Nome</span><span class="sxs-lookup"><span data-stu-id="a26b8-137">Name</span></span>           | <span data-ttu-id="a26b8-138">Tipo</span><span class="sxs-lookup"><span data-stu-id="a26b8-138">Type</span></span>   | <span data-ttu-id="a26b8-139">Necessário</span><span class="sxs-lookup"><span data-stu-id="a26b8-139">Required</span></span> | <span data-ttu-id="a26b8-140">Descrição</span><span class="sxs-lookup"><span data-stu-id="a26b8-140">Description</span></span>                                           |
|----------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="a26b8-141">id cliente</span><span class="sxs-lookup"><span data-stu-id="a26b8-141">customer-id</span></span>    | <span data-ttu-id="a26b8-142">string</span><span class="sxs-lookup"><span data-stu-id="a26b8-142">string</span></span> | <span data-ttu-id="a26b8-143">Sim</span><span class="sxs-lookup"><span data-stu-id="a26b8-143">Yes</span></span>      | <span data-ttu-id="a26b8-144">Uma cadeia formatada pelo GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="a26b8-144">A GUID-formatted string that identifies the customer.</span></span> |
| <span data-ttu-id="a26b8-145">devicebatch-id</span><span class="sxs-lookup"><span data-stu-id="a26b8-145">devicebatch-id</span></span> | <span data-ttu-id="a26b8-146">string</span><span class="sxs-lookup"><span data-stu-id="a26b8-146">string</span></span> | <span data-ttu-id="a26b8-147">Sim</span><span class="sxs-lookup"><span data-stu-id="a26b8-147">Yes</span></span>      | <span data-ttu-id="a26b8-148">Um identificador de cordas que identifica o lote do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a26b8-148">A string identifier that identifies the device batch.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="a26b8-149">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="a26b8-149">Request headers</span></span>

<span data-ttu-id="a26b8-150">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="a26b8-150">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="a26b8-151">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="a26b8-151">Request body</span></span>

<span data-ttu-id="a26b8-152">Nenhum</span><span class="sxs-lookup"><span data-stu-id="a26b8-152">None</span></span>

### <a name="request-example"></a><span data-ttu-id="a26b8-153">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="a26b8-153">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/47021739-3426-40bf-9601-61b4b6d7c793/deviceBatches/testbatch/devices HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e88d014d-ab70-41de-90a0-f7fd1797267d
MS-CorrelationId: de894e18-f027-4ac0-8b5a-34f0c222af0c
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="a26b8-154">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="a26b8-154">REST response</span></span>

<span data-ttu-id="a26b8-155">Se for bem sucedido, o corpo de resposta contém uma coleção paged de recursos do [Dispositivo.](device-deployment-resources.md#device)</span><span class="sxs-lookup"><span data-stu-id="a26b8-155">If successful, the response body contains a paged collection of [Device](device-deployment-resources.md#device) resources.</span></span> <span data-ttu-id="a26b8-156">A coleção contém 100 dispositivos numa página.</span><span class="sxs-lookup"><span data-stu-id="a26b8-156">The collection contains 100 devices in a page.</span></span> <span data-ttu-id="a26b8-157">Para recuperar a próxima página de 100 dispositivos, a continuaçãoToken no corpo de resposta deve ser incluída no pedido subsequente como cabeçalho MS-ContinuationToken.</span><span class="sxs-lookup"><span data-stu-id="a26b8-157">To retrieve the next page of 100 devices, the continuationToken in the response body must be included in the subsequent request as an MS-ContinuationToken header.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="a26b8-158">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="a26b8-158">Response success and error codes</span></span>

<span data-ttu-id="a26b8-159">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="a26b8-159">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="a26b8-160">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="a26b8-160">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="a26b8-161">Para obter uma lista completa, consulte [os códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="a26b8-161">For a full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="a26b8-162">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="a26b8-162">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1742
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 4a5002a2-0c1b-4e57-b491-dbcf19c0e7b8
MS-RequestId: 7b3e2e00-b330-4480-9d84-59ace713427f
MS-CV: YrLe3w6BbUSMt1fi.0
MS-ServerId: 030020344
Date: Tue, 25 Jul 2017 17:52:41 GMT

{
    "totalCount": 2,
    "items":
    [{
            "id": "7c141ea9-2816-4e15-a819-53f6856499ff",
            "serialNumber": "2R9-ZNP67",
            "productKey": "00329-00000-0003-AA6069",
            "modelName": "Precision WorkStation T7500",
            "oemManufacturerName":"Dell Inc.",
            "policies":[{
                    "key": "o_o_b_e",
                    "value": null
                }
            ],
            "uploadedDate":"2017-08-09T14:43:26.0092288-07:00",
            " attributes": {
                "objectType": "Device"
            }
        }, {
            "id": "e528a62f-5031-49f4-bea7-5fafe47388fd",
            "serialNumber": "1234567890",
            "productKey": "12345-67890-09876-54321-13579",
            "modelName": "HP Z420 Workstation",
            "oemManufacturerName": "Hewlett-Packard",
            "policies": [{
                    "key": "o_o_b_e",
                    "value": null
                }
            ],
            "uploadedDate": "2017-08-09T14:35:51.3126144-07:00",
            "attributes": {
                "objectType": "Device"
            }
        }
    ],
    "attributes": {
        "objectType": "Collection"
    }
}
```
