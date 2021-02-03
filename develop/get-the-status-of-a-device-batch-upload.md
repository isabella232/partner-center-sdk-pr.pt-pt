---
title: Obter o estado de um carregamento de lotes de dispositivos
description: Como obter o estado de um carregamento de lote de dispositivo para um cliente especificado.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: fb887ba257d6fbe68f95ae4b59d701ac4c934860
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/19/2020
ms.locfileid: "97769794"
---
# <a name="get-the-status-of-a-device-batch-upload"></a><span data-ttu-id="8dd16-103">Obter o estado de um carregamento de lotes de dispositivos</span><span class="sxs-lookup"><span data-stu-id="8dd16-103">Get the status of a device batch upload</span></span>

<span data-ttu-id="8dd16-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="8dd16-104">**Applies To**</span></span>

- <span data-ttu-id="8dd16-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="8dd16-105">Partner Center</span></span>
- <span data-ttu-id="8dd16-106">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="8dd16-106">Partner Center for Microsoft Cloud Germany</span></span>

<span data-ttu-id="8dd16-107">Como obter o estado de um carregamento de lote de dispositivo para um cliente especificado.</span><span class="sxs-lookup"><span data-stu-id="8dd16-107">How to get the status of a device batch upload for a specified customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8dd16-108">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="8dd16-108">Prerequisites</span></span>

- <span data-ttu-id="8dd16-109">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="8dd16-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="8dd16-110">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="8dd16-110">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="8dd16-111">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="8dd16-111">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="8dd16-112">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="8dd16-112">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="8dd16-113">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="8dd16-113">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="8dd16-114">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="8dd16-114">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="8dd16-115">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="8dd16-115">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="8dd16-116">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="8dd16-116">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="8dd16-117">O identificador de rastreio de lote devolvido no cabeçalho de localização quando o lote do dispositivo foi submetido.</span><span class="sxs-lookup"><span data-stu-id="8dd16-117">The batch tracking identifier returned in the Location header when the device batch was submitted.</span></span> <span data-ttu-id="8dd16-118">Para obter mais informações, consulte [a lista de dispositivos para o cliente especificado.](upload-a-list-of-devices-for-the-specified-customer.md)</span><span class="sxs-lookup"><span data-stu-id="8dd16-118">For more information, see [Upload a list of devices for the specified customer](upload-a-list-of-devices-for-the-specified-customer.md).</span></span>

## <a name="c"></a><span data-ttu-id="8dd16-119">C\#</span><span class="sxs-lookup"><span data-stu-id="8dd16-119">C\#</span></span>

<span data-ttu-id="8dd16-120">Para obter o estado de um carregamento de lote de dispositivo, ligue primeiro para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para recuperar uma interface para operações no cliente especificado.</span><span class="sxs-lookup"><span data-stu-id="8dd16-120">To get the status of a device batch upload, first call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to retrieve an interface to operations on the specified customer.</span></span> <span data-ttu-id="8dd16-121">Em seguida, ligue para o método [**BatchUploadStatus.ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.ibatchjobstatuscollection.byid) com o ID de rastreio do lote para obter uma interface para as operações de estado de upload de lotes.</span><span class="sxs-lookup"><span data-stu-id="8dd16-121">Then, call the [**BatchUploadStatus.ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.ibatchjobstatuscollection.byid) method with the batch tracking ID to get an interface to batch upload status operations.</span></span> <span data-ttu-id="8dd16-122">Por fim, ligue para o método [**Get**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.ibatchjobstatus.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.ibatchjobstatus.getasync) para recuperar o estado.</span><span class="sxs-lookup"><span data-stu-id="8dd16-122">Finally, call the [**Get**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.ibatchjobstatus.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.ibatchjobstatus.getasync) method to retrieve the status.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;
// string selectedTrackingId;

var status =
    partnerOperations.Customers.ById(selectedCustomerId).BatchUploadStatus.ById(selectedTrackingId).Get();
```

<span data-ttu-id="8dd16-123">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="8dd16-123">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="8dd16-124">**Projeto**: Partner Center SDK Samples **Class**: GetBatchUploadStatus.cs</span><span class="sxs-lookup"><span data-stu-id="8dd16-124">**Project**: Partner Center SDK Samples **Class**: GetBatchUploadStatus.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="8dd16-125">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="8dd16-125">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="8dd16-126">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="8dd16-126">Request syntax</span></span>

| <span data-ttu-id="8dd16-127">Método</span><span class="sxs-lookup"><span data-stu-id="8dd16-127">Method</span></span>  | <span data-ttu-id="8dd16-128">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="8dd16-128">Request URI</span></span>                                                                                                       |
|---------|-------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="8dd16-129">**Obter**</span><span class="sxs-lookup"><span data-stu-id="8dd16-129">**GET**</span></span> | <span data-ttu-id="8dd16-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/batchJobStatus/{batchtracking-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="8dd16-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/batchJobStatus/{batchtracking-id} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="8dd16-131">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="8dd16-131">URI parameter</span></span>

<span data-ttu-id="8dd16-132">Utilize os seguintes parâmetros de trajetória ao criar o pedido.</span><span class="sxs-lookup"><span data-stu-id="8dd16-132">Use the following path parameters when creating the request.</span></span>

| <span data-ttu-id="8dd16-133">Nome</span><span class="sxs-lookup"><span data-stu-id="8dd16-133">Name</span></span>             | <span data-ttu-id="8dd16-134">Tipo</span><span class="sxs-lookup"><span data-stu-id="8dd16-134">Type</span></span>   | <span data-ttu-id="8dd16-135">Necessário</span><span class="sxs-lookup"><span data-stu-id="8dd16-135">Required</span></span> | <span data-ttu-id="8dd16-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="8dd16-136">Description</span></span>                                                                                                                                                                    |
|------------------|--------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="8dd16-137">id cliente</span><span class="sxs-lookup"><span data-stu-id="8dd16-137">customer-id</span></span>      | <span data-ttu-id="8dd16-138">string</span><span class="sxs-lookup"><span data-stu-id="8dd16-138">string</span></span> | <span data-ttu-id="8dd16-139">Sim</span><span class="sxs-lookup"><span data-stu-id="8dd16-139">Yes</span></span>      | <span data-ttu-id="8dd16-140">Uma cadeia formatada pelo GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="8dd16-140">A GUID-formatted string that identifies the customer.</span></span>                                                                                                                          |
| <span data-ttu-id="8dd16-141">batchtracking-id</span><span class="sxs-lookup"><span data-stu-id="8dd16-141">batchtracking-id</span></span> | <span data-ttu-id="8dd16-142">string</span><span class="sxs-lookup"><span data-stu-id="8dd16-142">string</span></span> | <span data-ttu-id="8dd16-143">Sim</span><span class="sxs-lookup"><span data-stu-id="8dd16-143">Yes</span></span>      | <span data-ttu-id="8dd16-144">Um identificador formatado guid que é usado para recuperar o estado de upload do lote do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="8dd16-144">A GUID-formatted identifier that is used to retrieve a device batch upload status.</span></span> <span data-ttu-id="8dd16-145">Este ID é devolvido no cabeçalho localização quando o lote do dispositivo é submetido com sucesso.</span><span class="sxs-lookup"><span data-stu-id="8dd16-145">This ID is returned in the Location header when the device batch is successfully submitted.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="8dd16-146">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="8dd16-146">Request headers</span></span>

<span data-ttu-id="8dd16-147">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="8dd16-147">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="8dd16-148">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="8dd16-148">Request body</span></span>

<span data-ttu-id="8dd16-149">Nenhum</span><span class="sxs-lookup"><span data-stu-id="8dd16-149">None</span></span>

### <a name="request-example"></a><span data-ttu-id="8dd16-150">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="8dd16-150">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/47021739-3426-40bf-9601-61b4b6d7c793/batchjobstatus/0127ed8e-ff72-4983-a3d8-e8d8bd378932 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e88d014d-ab70-41de-90a0-f7fd1797267d
MS-CorrelationId: de894e18-f027-4ac0-8b5a-34f0c222af0c
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="8dd16-151">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="8dd16-151">REST response</span></span>

<span data-ttu-id="8dd16-152">Se for bem sucedida, a resposta contém um recurso [BatchUploadDetails.](device-deployment-resources.md#batchuploaddetails)</span><span class="sxs-lookup"><span data-stu-id="8dd16-152">If successful, the response contains a [BatchUploadDetails](device-deployment-resources.md#batchuploaddetails) resource.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="8dd16-153">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="8dd16-153">Response success and error codes</span></span>

<span data-ttu-id="8dd16-154">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="8dd16-154">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="8dd16-155">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="8dd16-155">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="8dd16-156">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="8dd16-156">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="8dd16-157">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="8dd16-157">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 400
MS-CorrelationId: 4a5002a2-0c1b-4e57-b491-dbcf19c0e7b8
MS-RequestId: 7b3e2e00-b330-4480-9d84-59ace713427f
MS-CV: YrLe3w6BbUSMt1fi.0
MS-ServerId: 030020344
Date: Tue, 25 Jul 2017 17:52:41 GMT

{
    "batchTrackingId": "0127ed8e-ff72-4983-a3d8-e8d8bd378932",
    "status": "finished",
    "startedTime": "2017-07-25T10:00:00",
    "completedTime": "2017-07-25T10:10:00",
    "devicesStatus": [{
            "serialNumber": "1234567890",
            "productKey": "12345-67890-09876-54321-13579",
            "status": "finished_with_errors",
            "errorCode": "808",
            "errorDescription": "ZtdDeviceAssignedToOtherTenant",
            "attributes": {
                "objectType": "DeviceUploadDetails"
            }
        }
    ],
    "attributes": {
        "objectType": "BatchUploadDetails"
    }
}
```
