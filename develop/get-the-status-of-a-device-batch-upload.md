---
title: Obter o estado de um carregamento de lotes de dispositivos
description: Como obter o estado de um carregamento de lote de dispositivo para um cliente especificado.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: fd8726af41fe4399797f39a0790cf962fde64acc
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/06/2021
ms.locfileid: "111548486"
---
# <a name="get-the-status-of-a-device-batch-upload"></a><span data-ttu-id="3f90c-103">Obter o estado de um carregamento de lotes de dispositivos</span><span class="sxs-lookup"><span data-stu-id="3f90c-103">Get the status of a device batch upload</span></span>

<span data-ttu-id="3f90c-104">**Aplica-se a**: Partner Center | Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="3f90c-104">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany</span></span>

<span data-ttu-id="3f90c-105">Como obter o estado de um carregamento de lote de dispositivo para um cliente especificado.</span><span class="sxs-lookup"><span data-stu-id="3f90c-105">How to get the status of a device batch upload for a specified customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3f90c-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="3f90c-106">Prerequisites</span></span>

- <span data-ttu-id="3f90c-107">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="3f90c-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="3f90c-108">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="3f90c-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="3f90c-109">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="3f90c-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="3f90c-110">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="3f90c-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="3f90c-111">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="3f90c-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="3f90c-112">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="3f90c-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="3f90c-113">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="3f90c-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="3f90c-114">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="3f90c-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="3f90c-115">O identificador de rastreio de lote devolvido no cabeçalho de localização quando o lote do dispositivo foi submetido.</span><span class="sxs-lookup"><span data-stu-id="3f90c-115">The batch tracking identifier returned in the Location header when the device batch was submitted.</span></span> <span data-ttu-id="3f90c-116">Para obter mais informações, consulte [a lista de dispositivos para o cliente especificado.](upload-a-list-of-devices-for-the-specified-customer.md)</span><span class="sxs-lookup"><span data-stu-id="3f90c-116">For more information, see [Upload a list of devices for the specified customer](upload-a-list-of-devices-for-the-specified-customer.md).</span></span>

## <a name="c"></a><span data-ttu-id="3f90c-117">C\#</span><span class="sxs-lookup"><span data-stu-id="3f90c-117">C\#</span></span>

<span data-ttu-id="3f90c-118">Para obter o estado de um carregamento de lote de dispositivo, ligue primeiro para o método [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para recuperar uma interface para operações no cliente especificado.</span><span class="sxs-lookup"><span data-stu-id="3f90c-118">To get the status of a device batch upload, first call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to retrieve an interface to operations on the specified customer.</span></span> <span data-ttu-id="3f90c-119">Em seguida, ligue para o método [**BatchUploadStatus.ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.ibatchjobstatuscollection.byid) com o ID de rastreio do lote para obter uma interface para as operações de estado de upload de lotes.</span><span class="sxs-lookup"><span data-stu-id="3f90c-119">Then, call the [**BatchUploadStatus.ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.ibatchjobstatuscollection.byid) method with the batch tracking ID to get an interface to batch upload status operations.</span></span> <span data-ttu-id="3f90c-120">Por fim, ligue para o método [**Get**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.ibatchjobstatus.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.ibatchjobstatus.getasync) para recuperar o estado.</span><span class="sxs-lookup"><span data-stu-id="3f90c-120">Finally, call the [**Get**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.ibatchjobstatus.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.ibatchjobstatus.getasync) method to retrieve the status.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;
// string selectedTrackingId;

var status =
    partnerOperations.Customers.ById(selectedCustomerId).BatchUploadStatus.ById(selectedTrackingId).Get();
```

<span data-ttu-id="3f90c-121">**Amostra**: [App de teste de consola](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="3f90c-121">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="3f90c-122">**Project**: Partner Center SDK Samples **Class**: GetBatchUploadStatus.cs</span><span class="sxs-lookup"><span data-stu-id="3f90c-122">**Project**: Partner Center SDK Samples **Class**: GetBatchUploadStatus.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="3f90c-123">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="3f90c-123">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="3f90c-124">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="3f90c-124">Request syntax</span></span>

| <span data-ttu-id="3f90c-125">Método</span><span class="sxs-lookup"><span data-stu-id="3f90c-125">Method</span></span>  | <span data-ttu-id="3f90c-126">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="3f90c-126">Request URI</span></span>                                                                                                       |
|---------|-------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="3f90c-127">**Obter**</span><span class="sxs-lookup"><span data-stu-id="3f90c-127">**GET**</span></span> | <span data-ttu-id="3f90c-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/batchJobStatus/{batchtracking-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="3f90c-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/batchJobStatus/{batchtracking-id} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="3f90c-129">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="3f90c-129">URI parameter</span></span>

<span data-ttu-id="3f90c-130">Utilize os seguintes parâmetros de trajetória ao criar o pedido.</span><span class="sxs-lookup"><span data-stu-id="3f90c-130">Use the following path parameters when creating the request.</span></span>

| <span data-ttu-id="3f90c-131">Nome</span><span class="sxs-lookup"><span data-stu-id="3f90c-131">Name</span></span>             | <span data-ttu-id="3f90c-132">Tipo</span><span class="sxs-lookup"><span data-stu-id="3f90c-132">Type</span></span>   | <span data-ttu-id="3f90c-133">Necessário</span><span class="sxs-lookup"><span data-stu-id="3f90c-133">Required</span></span> | <span data-ttu-id="3f90c-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="3f90c-134">Description</span></span>                                                                                                                                                                    |
|------------------|--------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="3f90c-135">id cliente</span><span class="sxs-lookup"><span data-stu-id="3f90c-135">customer-id</span></span>      | <span data-ttu-id="3f90c-136">string</span><span class="sxs-lookup"><span data-stu-id="3f90c-136">string</span></span> | <span data-ttu-id="3f90c-137">Yes</span><span class="sxs-lookup"><span data-stu-id="3f90c-137">Yes</span></span>      | <span data-ttu-id="3f90c-138">Uma cadeia formatada pelo GUID que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="3f90c-138">A GUID-formatted string that identifies the customer.</span></span>                                                                                                                          |
| <span data-ttu-id="3f90c-139">batchtracking-id</span><span class="sxs-lookup"><span data-stu-id="3f90c-139">batchtracking-id</span></span> | <span data-ttu-id="3f90c-140">string</span><span class="sxs-lookup"><span data-stu-id="3f90c-140">string</span></span> | <span data-ttu-id="3f90c-141">Yes</span><span class="sxs-lookup"><span data-stu-id="3f90c-141">Yes</span></span>      | <span data-ttu-id="3f90c-142">Um identificador formatado guid que é usado para recuperar o estado de upload do lote do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="3f90c-142">A GUID-formatted identifier that is used to retrieve a device batch upload status.</span></span> <span data-ttu-id="3f90c-143">Este ID é devolvido no cabeçalho localização quando o lote do dispositivo é submetido com sucesso.</span><span class="sxs-lookup"><span data-stu-id="3f90c-143">This ID is returned in the Location header when the device batch is successfully submitted.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="3f90c-144">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="3f90c-144">Request headers</span></span>

<span data-ttu-id="3f90c-145">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="3f90c-145">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="3f90c-146">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="3f90c-146">Request body</span></span>

<span data-ttu-id="3f90c-147">Nenhuma</span><span class="sxs-lookup"><span data-stu-id="3f90c-147">None</span></span>

### <a name="request-example"></a><span data-ttu-id="3f90c-148">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="3f90c-148">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/47021739-3426-40bf-9601-61b4b6d7c793/batchjobstatus/0127ed8e-ff72-4983-a3d8-e8d8bd378932 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e88d014d-ab70-41de-90a0-f7fd1797267d
MS-CorrelationId: de894e18-f027-4ac0-8b5a-34f0c222af0c
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="3f90c-149">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="3f90c-149">REST response</span></span>

<span data-ttu-id="3f90c-150">Se for bem sucedida, a resposta contém um recurso [BatchUploadDetails.](device-deployment-resources.md#batchuploaddetails)</span><span class="sxs-lookup"><span data-stu-id="3f90c-150">If successful, the response contains a [BatchUploadDetails](device-deployment-resources.md#batchuploaddetails) resource.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="3f90c-151">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="3f90c-151">Response success and error codes</span></span>

<span data-ttu-id="3f90c-152">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="3f90c-152">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="3f90c-153">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="3f90c-153">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="3f90c-154">Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="3f90c-154">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="3f90c-155">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="3f90c-155">Response example</span></span>

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
