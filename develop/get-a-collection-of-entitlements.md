---
title: Obter uma coleção de elegibilidade
description: Como obter uma coleção de direitos.
ms.date: 01/28/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 7bb8d3aefb11fae0af4bce790b41598d935de57c
ms.sourcegitcommit: d20e7d572fee09a83a4b23a92da7ff09cfebe75a
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/10/2021
ms.locfileid: "111906417"
---
# <a name="get-a-collection-of-entitlements"></a><span data-ttu-id="a8f01-103">Obter uma coleção de elegibilidade</span><span class="sxs-lookup"><span data-stu-id="a8f01-103">Get a collection of entitlements</span></span>

<span data-ttu-id="a8f01-104">Como obter uma coleção de direitos.</span><span class="sxs-lookup"><span data-stu-id="a8f01-104">How to get a collection of entitlements.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a8f01-105">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="a8f01-105">Prerequisites</span></span>

- <span data-ttu-id="a8f01-106">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="a8f01-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="a8f01-107">Este cenário suporta a autenticação com credenciais app+utilizador.</span><span class="sxs-lookup"><span data-stu-id="a8f01-107">This scenario supports authentication with App+User credentials.</span></span>

- <span data-ttu-id="a8f01-108">Um ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="a8f01-108">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="a8f01-109">Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="a8f01-109">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="a8f01-110">Selecione **CSP** no menu Partner Center, seguido de **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="a8f01-110">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="a8f01-111">Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.**</span><span class="sxs-lookup"><span data-stu-id="a8f01-111">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="a8f01-112">Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.**</span><span class="sxs-lookup"><span data-stu-id="a8f01-112">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="a8f01-113">O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="a8f01-113">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="a8f01-114">C\#</span><span class="sxs-lookup"><span data-stu-id="a8f01-114">C\#</span></span>

<span data-ttu-id="a8f01-115">Para obter uma recolha de direitos para um cliente, obtenha uma interface para operações [**de Direito,**](entitlement-resources.md#entitlement) ligando para o método  [**IAggregatePartner.Customers.ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o ID do cliente para identificar o cliente.</span><span class="sxs-lookup"><span data-stu-id="a8f01-115">To get an entitlements collection for a customer, obtain an interface to [**Entitlement**](entitlement-resources.md#entitlement) operations by calling the  [**IAggregatePartner.Customers.ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="a8f01-116">Em seguida, recupere a interface da propriedade **Entitlements** e ligue para o método **Get()** ou **GetAsync(para** recuperar a recolha de direitos.</span><span class="sxs-lookup"><span data-stu-id="a8f01-116">Then, retrieve the interface from the **Entitlements** property and call the **Get()** or **GetAsync()** method to retrieve the collection of entitlements.</span></span>

``` csharp
IAggregatePartner partnerOperations;
string customerId;

// Get the collection of entitlements.
var entitlements = partnerOperations.Customers.ById(customerId).Entitlements.Get();
```

<span data-ttu-id="a8f01-117">Para preencher as datas de validade para os direitos a serem recuperados, ligue para os mesmos métodos acima e desconte o parâmetro boolean opcional **mostrarExpiry** a verdadeiro **Get (verdadeiro)** ou **GetAsync (verdade)**.</span><span class="sxs-lookup"><span data-stu-id="a8f01-117">To populate expiry dates for the entitlements to be retrieved, call the same methods above and set the optional boolean parameter **showExpiry** to true **Get(true)** or **GetAsync(true)**.</span></span> <span data-ttu-id="a8f01-118">Isto indica que são necessárias datas de validade do direito (quando aplicável).</span><span class="sxs-lookup"><span data-stu-id="a8f01-118">This indicates that entitlement expiry dates are required (when applicable).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a8f01-119">Os tipos de direito no local não têm datas de validade.</span><span class="sxs-lookup"><span data-stu-id="a8f01-119">On-premise entitlement types do not have expiry dates.</span></span>

## <a name="rest-request"></a><span data-ttu-id="a8f01-120">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="a8f01-120">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="a8f01-121">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="a8f01-121">Request syntax</span></span>

| <span data-ttu-id="a8f01-122">Método</span><span class="sxs-lookup"><span data-stu-id="a8f01-122">Method</span></span> | <span data-ttu-id="a8f01-123">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="a8f01-123">Request URI</span></span> |
|--------|-------------|
| <span data-ttu-id="a8f01-124">**Obter**</span><span class="sxs-lookup"><span data-stu-id="a8f01-124">**GET**</span></span> | <span data-ttu-id="a8f01-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{clienteId}/direitos HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="a8f01-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customerId}/entitlements HTTP/1.1</span></span>                            |

### <a name="uri-parameters"></a><span data-ttu-id="a8f01-126">Parâmetros URI</span><span class="sxs-lookup"><span data-stu-id="a8f01-126">URI parameters</span></span>

<span data-ttu-id="a8f01-127">Utilize os seguintes parâmetros de percurso e consulta ao criar o pedido.</span><span class="sxs-lookup"><span data-stu-id="a8f01-127">Use the following path and query parameters when creating the request.</span></span>

| <span data-ttu-id="a8f01-128">Nome</span><span class="sxs-lookup"><span data-stu-id="a8f01-128">Name</span></span> | <span data-ttu-id="a8f01-129">Tipo</span><span class="sxs-lookup"><span data-stu-id="a8f01-129">Type</span></span> | <span data-ttu-id="a8f01-130">Necessário</span><span class="sxs-lookup"><span data-stu-id="a8f01-130">Required</span></span> | <span data-ttu-id="a8f01-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="a8f01-131">Description</span></span> |
|------|------|----------|-------------|
| <span data-ttu-id="a8f01-132">customerId</span><span class="sxs-lookup"><span data-stu-id="a8f01-132">customerId</span></span> | <span data-ttu-id="a8f01-133">string</span><span class="sxs-lookup"><span data-stu-id="a8f01-133">string</span></span> | <span data-ttu-id="a8f01-134">Yes</span><span class="sxs-lookup"><span data-stu-id="a8f01-134">Yes</span></span> | <span data-ttu-id="a8f01-135">Um cliente formatado GUIDId que identifica o cliente.</span><span class="sxs-lookup"><span data-stu-id="a8f01-135">A GUID formatted customerId that identifies the customer.</span></span> |
| <span data-ttu-id="a8f01-136">DireitoTipo</span><span class="sxs-lookup"><span data-stu-id="a8f01-136">entitlementType</span></span> | <span data-ttu-id="a8f01-137">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="a8f01-137">string</span></span> | <span data-ttu-id="a8f01-138">No</span><span class="sxs-lookup"><span data-stu-id="a8f01-138">No</span></span> | <span data-ttu-id="a8f01-139">Pode ser usado para especificar o tipo de direitos a recuperar **(software** ou **reservaInstance).**</span><span class="sxs-lookup"><span data-stu-id="a8f01-139">Can be used to specify the type of entitlements to be retrieved (**software** or **reservedInstance** ).</span></span> <span data-ttu-id="a8f01-140">Se não estiver definido, todos os tipos serão recuperados</span><span class="sxs-lookup"><span data-stu-id="a8f01-140">If not set, all types will be retrieved</span></span> |
| <span data-ttu-id="a8f01-141">showExpiry</span><span class="sxs-lookup"><span data-stu-id="a8f01-141">showExpiry</span></span> | <span data-ttu-id="a8f01-142">boolean</span><span class="sxs-lookup"><span data-stu-id="a8f01-142">boolean</span></span> | <span data-ttu-id="a8f01-143">No</span><span class="sxs-lookup"><span data-stu-id="a8f01-143">No</span></span> | <span data-ttu-id="a8f01-144">Bandeira opcional que indica se são necessárias datas de validade dos direitos.</span><span class="sxs-lookup"><span data-stu-id="a8f01-144">Optional flag that indicates if entitlements expiry dates are required.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="a8f01-145">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="a8f01-145">Request headers</span></span>

<span data-ttu-id="a8f01-146">Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="a8f01-146">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="a8f01-147">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="a8f01-147">Request body</span></span>

<span data-ttu-id="a8f01-148">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="a8f01-148">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="a8f01-149">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="a8f01-149">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/18ac2950-8ea9-4dfc-92a4-ff4d4cd57796/entitlements HTTP/1.1
Authorization: Bearer <Token>
Accept: application/json
MS-RequestId: cdc428d2-035b-41c4-9a32-e643c4471cbd
MS-CorrelationId: 799eee8d-07d1-452a-a035-388259df137c
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="a8f01-150">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="a8f01-150">REST response</span></span>

<span data-ttu-id="a8f01-151">Se for bem sucedido, o organismo de resposta contém uma coleção de recursos de [direito.](entitlement-resources.md#entitlement)</span><span class="sxs-lookup"><span data-stu-id="a8f01-151">If successful, the response body contains a collection of [Entitlement](entitlement-resources.md#entitlement) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="a8f01-152">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="a8f01-152">Response success and error codes</span></span>

<span data-ttu-id="a8f01-153">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="a8f01-153">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="a8f01-154">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="a8f01-154">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="a8f01-155">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="a8f01-155">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="a8f01-156">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="a8f01-156">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 103778
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 799eee8d-07d1-452a-a035-388259df137c
MS-RequestId: cdc428d2-035b-41c4-9a32-e643c4471cbd
X-Locale: en-US
MS-CV: EjFdw8fCpkKyMyza.0
MS-ServerId: 000002
Date: Mon, 19 Mar 2018 07:42:51 GMT

{
  "totalCount": 2,
  "items": [
    {
      "includedEntitlements": [],
      "referenceOrder": {
        "id": "KaJ8XvkKc_GoNZOUyjVaRJalTBN5MWdV1",
        "lineItemId": "0"
      },
      "productId": "DZH318Z0BQ3W",
      "quantity": 1,
      "entitledArtifacts": [
        {
          "link": {
            "uri": "/customers/18ac2950-8ea9-4dfc-92a4-ff4d4cd57796/artifacts/reservedinstance/groups/2caf524395724e638ef64e109f1f79ca/lineitems/03500b1b-f2d6-4e23-ab4b-9fd67b917012/resource/ebf2e74b-630e-4a09-857d-a1f6c6351336",
            "method": "GET",
            "headers": []
          },
          "resourceId": "ebf2e74b-630e-4a09-857d-a1f6c6351336",
          "artifactType": "reservedinstance"
        }
      ],
      "skuId": "007J",
      "entitlementType": "reservedinstance"
      "dynamicAttributes": {
               "reservationType": "virtualmachines"
        }
    },
    {
      "includedEntitlements": [
        {
          "includedEntitlements": [],
          "referenceOrder": {
              "id": "NUXMSvmS20EQ4kFsZmzkSqb747fqKmNk1",
              "lineItemId": "0"
          },
          "productId": "DG7GMGF0DWTJ",
          "quantity": 1,
          "entitledArtifacts": [],
          "skuId": "0001",
          "entitlementType": "software"
        },
        {
          "includedEntitlements": [],
          "referenceOrder": {
            "id": "NUXMSvmS20EQ4kFsZmzkSqb747fqKmNk1",
            "lineItemId": "0"
          },
            "productId": "DG7GMGF0DWLG",
            "quantity": 1,
            "entitledArtifacts": [],
            "skuId": "0002",
            "entitlementType": "software"
          }
        ],
        "referenceOrder": {
          "id": "NUXMSvmS20EQ4kFsZmzkSqb747fqKmNk1",
          "lineItemId": "0"
        },
        "productId": "DG7GMGF0DWTK",
        "quantity": 1,
        "entitledArtifacts": [],
        "skuId": "0002",
        "entitlementType": "software"
    }
  ],
  "attributes": {
    "objectType": "Collection"
  }
}
```

## <a name="additional-examples"></a><span data-ttu-id="a8f01-157">Exemplos adicionais</span><span class="sxs-lookup"><span data-stu-id="a8f01-157">Additional Examples</span></span>

<span data-ttu-id="a8f01-158">O exemplo a seguir mostra como recuperar um tipo específico de direitos juntamente com datas de validade (quando aplicável)</span><span class="sxs-lookup"><span data-stu-id="a8f01-158">The following example shows you how to retrieve a specific type of entitlements along with expiry dates (when applicable)</span></span>

### <a name="c-example"></a><span data-ttu-id="a8f01-159">Exemplo \# C</span><span class="sxs-lookup"><span data-stu-id="a8f01-159">C\# example</span></span>

<span data-ttu-id="a8f01-160">Para recuperar um tipo específico de direitos, obtenha a interface **ByEntitlementType** a partir da interface Entitlements e utilize os **métodos** **Get()** ou **GetAsync().**</span><span class="sxs-lookup"><span data-stu-id="a8f01-160">To retrieve a specific type of entitlements, obtain the **ByEntitlementType** interface from the **Entitlements** interface and use the **Get()** or **GetAsync()** methods.</span></span>

``` csharp
ResourceCollection<Entitlement> entitlements = partnerOperations.Customers.ById(selectedCustomerId).Entitlements.ByEntitlementType("software").Get(true);
```

### <a name="request-example"></a><span data-ttu-id="a8f01-161">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="a8f01-161">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/de3dcef9-9991-459c-ac71-2903d1127414/entitlements?entitlementtype=software&showExpiry=true
Authorization: Bearer <Token>
Accept: application/json
MS-RequestId: 6517a410-67ce-4995-9bb7-116a52179f92
MS-CorrelationId: d9eb8194-9b99-4057-a2fe-98bdf05f013c
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

### <a name="response-example"></a><span data-ttu-id="a8f01-162">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="a8f01-162">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1791
Content-Type: application/json; charset=utf-8
MS-CorrelationId: d9eb8194-9b99-4057-a2fe-98bdf05f013c
MS-RequestId: 6517a410-67ce-4995-9bb7-116a52179f92
X-Locale: en-US
MS-CV: yD+4LBKePUSp/vqJ.0
MS-ServerId: 000002
Date: Mon, 28 Jan 2019 18:31:43 GMT

{
    "totalCount": 2,
    "items": [
        {
            "includedEntitlements": [
                {
                    "includedEntitlements": [],
                    "referenceOrder": {
                        "id": "4teYMtWYEeKM77JftGLIQYMOZPTwyOEV1",
                        "lineItemId": "0",
                        "alternateId": "8f3af3dea1ea"
                    },
                    "productId": "DG7GMGF0DWM2",
                    "quantity": 1,
                    "entitledArtifacts": [],
                    "skuId": "0001",
                    "entitlementType": "software"
                },
                {
                    "includedEntitlements": [],
                    "referenceOrder": {
                        "id": "4teYMtWYEeKM77JftGLIQYMOZPTwyOEV1",
                        "lineItemId": "0",
                        "alternateId": "8f3af3dea1ea"
                    },
                    "productId": "DG7GMGF0DWMK",
                    "quantity": 1,
                    "entitledArtifacts": [],
                    "skuId": "0001",
                    "entitlementType": "software"
                }
            ],
            "referenceOrder": {
                "id": "4teYMtWYEeKM77JftGLIQYMOZPTwyOEV1",
                "lineItemId": "0",
                "alternateId": "8f3af3dea1ea"
            },
            "productId": "DG7GMGF0DWM3",
            "quantity": 1,
            "entitledArtifacts": [],
            "skuId": "0002",
            "entitlementType": "software"
        },
        {
            "includedEntitlements": [
                {
                    "includedEntitlements": [],
                    "referenceOrder": {
                        "id": "4teYMtWYEeKM77JftGLIQYMOZPTwyOEV1",
                        "lineItemId": "1",
                        "alternateId": "8f3af3dea1ea"
                    },
                    "productId": "DG7GMGF0DWV1",
                    "quantity": 1,
                    "entitledArtifacts": [],
                    "skuId": "0002",
                    "entitlementType": "software"
                },
                {
                    "includedEntitlements": [],
                    "referenceOrder": {
                        "id": "4teYMtWYEeKM77JftGLIQYMOZPTwyOEV1",
                        "lineItemId": "1",
                        "alternateId": "8f3af3dea1ea"
                    },
                    "productId": "DG7GMGF0DWV2",
                    "quantity": 1,
                    "entitledArtifacts": [],
                    "skuId": "0002",
                    "entitlementType": "software"
                }
            ],
            "referenceOrder": {
                "id": "4teYMtWYEeKM77JftGLIQYMOZPTwyOEV1",
                "lineItemId": "1",
                "alternateId": "8f3af3dea1ea"
            },
            "productId": "DG7GMGF0DWBQ",
            "quantity": 1,
            "entitledArtifacts": [],
            "skuId": "0003",
            "entitlementType": "software",
            "expiryDate": "2022-01-28T00:00:00Z"
        }
    ],
    "attributes": {
        "objectType": "Collection"
    }
}
```

<span data-ttu-id="a8f01-163">Os exemplos que se seguem mostram-lhe como recuperar informações sobre produtos e reservas a partir de um direito.</span><span class="sxs-lookup"><span data-stu-id="a8f01-163">The following examples show you how to retrieve information about products and reservations from an entitlement.</span></span>

### <a name="retrieve-virtual-machine-reservation-details-from-an-entitlement-by-using-sdk-v18"></a><span data-ttu-id="a8f01-164">Recupere os detalhes da reserva de máquina virtual a partir de um direito usando SDK V1.8</span><span class="sxs-lookup"><span data-stu-id="a8f01-164">Retrieve virtual machine reservation details from an entitlement by using SDK V1.8</span></span>

### <a name="c-example"></a><span data-ttu-id="a8f01-165">Exemplo \# C</span><span class="sxs-lookup"><span data-stu-id="a8f01-165">C\# example</span></span>

<span data-ttu-id="a8f01-166">Para obter mais detalhes relacionados com as reservas de máquinas virtuais a partir de um direito, invoque o URI exposto sob entitledArtifacts.link com artefactoType = virtual_machine_reserved_instance.</span><span class="sxs-lookup"><span data-stu-id="a8f01-166">To retrieve more details related to the virtual machine reservations from an entitlement, invoke the URI exposed under entitledArtifacts.link with artifactType = virtual_machine_reserved_instance.</span></span>

``` csharp
ResourceCollection<Entitlement> entitlements = partnerOperations.Customers.ById(selectedCustomerId).Entitlements.ByEntitlementType("VirtualMachineReservedInstance").Get();

((VirtualMachineReservedInstanceArtifact)entitlements.First().EntitledArtifacts.First(x => x.Type == ArtifactType.VirtualMachineReservedInstance)).Link.InvokeAsync<VirtualMachineReservedInstanceArtifactDetails>(partnerOperations)
```

### <a name="request-example"></a><span data-ttu-id="a8f01-167">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="a8f01-167">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/18ac2950-8ea9-4dfc-92a4-ff4d4cd57796/artifacts/virtualmachinereservedinstance/groups/2caf524395724e638ef64e109f1f79ca/lineitems/03500b1b-f2d6-4e23-ab4b-9fd67b917012/resource/ebf2e74b-630e-4a09-857d-a1f6c6351336 HTTP/1.1
Authorization: Bearer <Token>
Accept: application/json
MS-RequestId: cdc428d2-035b-41c4-9a32-e643c4471cbd
MS-CorrelationId: 799eee8d-07d1-452a-a035-388259df137c
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

### <a name="response-example"></a><span data-ttu-id="a8f01-168">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="a8f01-168">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 368
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 799eee8d-07d1-452a-a035-388259df137c
MS-RequestId: cdc428d2-035b-41c4-9a32-e643c4471cbd
X-Locale: en-US
MS-CV: yrdTGsZ7IU2v9okv.0
MS-ServerId: 000002
Date: Mon, 19 Mar 2018 07:45:14 GMT

{
  "type": "virtual_machine_reserved_instance",
  "virtualMachineReservations": [
    {
      "reservationId": "99f320db-c029-4c1b-a157-dad76e4481b6",
      "scopeType": "Shared",
      "quantity": 1,
      "expiryDateTime": "2019-02-23T00:00:00",
      "effectiveDateTime": "2018-02-23T18:15:24.6724884Z",
      "provisioningState": "Created"
    }
  ]
}
```

### <a name="retrieve-reservation-details-from-an-entitlement-by-using-sdk-v19"></a><span data-ttu-id="a8f01-169">Recupere os detalhes da reserva a partir de um direito utilizando SDK V1.9</span><span class="sxs-lookup"><span data-stu-id="a8f01-169">Retrieve reservation details from an entitlement by using SDK V1.9</span></span>

### <a name="c-example"></a><span data-ttu-id="a8f01-170">Exemplo \# C</span><span class="sxs-lookup"><span data-stu-id="a8f01-170">C\# example</span></span>

<span data-ttu-id="a8f01-171">Para obter mais detalhes relacionados com as reservas de um direito de instância reservado, invoque o URI exposto ```entitledArtifacts.link``` a ```artifactType = reservedinstance``` .</span><span class="sxs-lookup"><span data-stu-id="a8f01-171">To retrieve more details related to the reservations from a reserved instance entitlement, invoke the URI exposed under ```entitledArtifacts.link``` with ```artifactType = reservedinstance```.</span></span>

``` csharp
ResourceCollection<Entitlement> entitlements = partnerOperations.Customers.ById(selectedCustomerId).Entitlements.ByEntitlementType("ReservedInstance").Get();

((ReservedInstanceArtifact)entitlements.First().EntitledArtifacts.First(x => x.Type == ArtifactType.ReservedInstance)).Link.InvokeAsync<ReservedInstanceArtifactDetails>(partnerOperations);
```

### <a name="request-example"></a><span data-ttu-id="a8f01-172">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="a8f01-172">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/18ac2950-8ea9-4dfc-92a4-ff4d4cd57796/artifacts/reservedinstance/groups/2caf524395724e638ef64e109f1f79ca/lineitems/03500b1b-f2d6-4e23-ab4b-9fd67b917012/resource/ebf2e74b-630e-4a09-857d-a1f6c6351336 HTTP/1.1
Authorization: Bearer <Token>
Accept: application/json
MS-RequestId: cdc428d2-035b-41c4-9a32-e643c4471cbd
MS-CorrelationId: 799eee8d-07d1-452a-a035-388259df137c
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

### <a name="response-example"></a><span data-ttu-id="a8f01-173">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="a8f01-173">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 368
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 799eee8d-07d1-452a-a035-388259df137c
MS-RequestId: cdc428d2-035b-41c4-9a32-e643c4471cbd
X-Locale: en-US
MS-CV: yrdTGsZ7IU2v9okv.0
MS-ServerId: 000002
Date: Mon, 19 Mar 2018 07:45:14 GMT

{
  "type": "reservedinstance",
  "virtualMachineReservations": [
    {
      "reservationId": "99f320db-c029-4c1b-a157-dad76e4481b6",
      "scopeType": "Shared",
      "quantity": 1,
      "expiryDateTime": "2019-02-23T00:00:00",
      "effectiveDateTime": "2018-02-23T18:15:24.6724884Z",
      "provisioningState": "Created"
    }
  ]
}
```

### <a name="api-consumers"></a><span data-ttu-id="a8f01-174">Consumidores API</span><span class="sxs-lookup"><span data-stu-id="a8f01-174">API Consumers</span></span>

<span data-ttu-id="a8f01-175">Parceiros que estão a usar a API para consultar direitos de instância reservados à máquina virtual - Atualize o pedido URI de **/clientes/{customerId}/direitos a /cliente/{clienteD}/direitos?entitlementType=virtualmachinereservinstance** para manter a compatibilidade para trás.</span><span class="sxs-lookup"><span data-stu-id="a8f01-175">Partners who are using the API to query virtual machine reserved instance entitlements - Update the request URI from **/customers/{customerId}/entitlements to /customers/{customerId}/entitlements?entitlementType=virtualmachinereservedinstance** to maintain backward compatibility.</span></span> <span data-ttu-id="a8f01-176">Para consumir máquina virtual ou Azure SQL com contrato melhorado, atualize o pedido URI a **/clientes/{clienteId}/direitos?entitlementType=reservedinstance**.</span><span class="sxs-lookup"><span data-stu-id="a8f01-176">To consume virtual machine or Azure SQL with enhanced contract, update the request URI to **/customers/{customerId}/entitlements?entitlementType=reservedinstance**.</span></span>
