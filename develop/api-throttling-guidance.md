---
title: Documentação de orientação da limitação de largura de banda da API
description: Para os parceiros que chamam APIs do Partner Center, saiba quais as APIs que são impactadas pelo estrangulamento da Microsoft API e pelas melhores práticas para evitar ou lidar melhor com o estrangulamento.
ms.date: 09/09/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: vijvala
ms.author: vijvala
ms.openlocfilehash: a52751a97e699050075c1aac910cc51e94514f26
ms.sourcegitcommit: 01e75175077611da92175c777a440a594fb05797
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/08/2020
ms.locfileid: "97770232"
---
# <a name="api-throttling-guidance-for-partners-calling-partner-center-apis"></a><span data-ttu-id="beaa9-103">API acelera orientação para parceiros que chamam APIs do Partner Center</span><span class="sxs-lookup"><span data-stu-id="beaa9-103">API throttling guidance for partners calling Partner Center APIs</span></span> 

<span data-ttu-id="beaa9-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="beaa9-104">**Applies to**</span></span>

- <span data-ttu-id="beaa9-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="beaa9-105">Partner Center</span></span>

<span data-ttu-id="beaa9-106">A Microsoft está a implementar o estrangulamento da API para permitir um desempenho mais consistente dentro de um período de tempo para os parceiros que chamam as APIs do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="beaa9-106">Microsoft is implementing API throttling to allow more consistent performance within a time span for partners calling the Partner Center APIs.</span></span> <span data-ttu-id="beaa9-107">O estrangulamento limita o número de pedidos a um serviço num período de tempo para evitar o uso excessivo de recursos.</span><span class="sxs-lookup"><span data-stu-id="beaa9-107">Throttling limits the number of requests to a service in a time span to prevent overuse of resources.</span></span> <span data-ttu-id="beaa9-108">Enquanto o Partner Center é projetado para lidar com um grande volume de pedidos, se um número esmagador de pedidos ocorrer por poucos parceiros, o estrangulamento ajuda a manter o melhor desempenho e fiabilidade para todos os parceiros.</span><span class="sxs-lookup"><span data-stu-id="beaa9-108">While Partner Center is designed to handle a high volume of requests, if an overwhelming number of requests occur by few partners, throttling helps maintain optimal performance and reliability for all partners.</span></span>  

<span data-ttu-id="beaa9-109">Os limites de estrangulamento variam em função do cenário.</span><span class="sxs-lookup"><span data-stu-id="beaa9-109">Throttling limits vary based on the scenario.</span></span> <span data-ttu-id="beaa9-110">Por exemplo, se estiver a executar um grande volume de escritas, a possibilidade de estrangulamento é maior do que se estiver apenas a executar leituras.</span><span class="sxs-lookup"><span data-stu-id="beaa9-110">For example, if you are performing a large volume of writes, the possibility for throttling is higher than if you are only performing reads.</span></span>

## <a name="what-happens-when-throttling-occurs"></a><span data-ttu-id="beaa9-111">O que acontece quando o estrangulamento ocorre?</span><span class="sxs-lookup"><span data-stu-id="beaa9-111">What happens when throttling occurs?</span></span> 

<span data-ttu-id="beaa9-112">Quando um limiar de estrangulamento é ultrapassado, o Partner Center limita quaisquer pedidos adicionais desse cliente por um período de tempo.</span><span class="sxs-lookup"><span data-stu-id="beaa9-112">When a throttling threshold is exceeded, Partner Center limits any further requests from that client for a period of time.</span></span> <span data-ttu-id="beaa9-113">O comportamento de estrangulamento depende do tipo e do número de pedidos.</span><span class="sxs-lookup"><span data-stu-id="beaa9-113">Throttling behavior depends on the type and number of requests.</span></span>   

### <a name="common-throttling-scenarios"></a><span data-ttu-id="beaa9-114">Cenários comuns de estrangulamento</span><span class="sxs-lookup"><span data-stu-id="beaa9-114">Common throttling scenarios</span></span> 

<span data-ttu-id="beaa9-115">As causas mais comuns de estrangulamento dos clientes incluem:</span><span class="sxs-lookup"><span data-stu-id="beaa9-115">The most common causes of throttling of clients include:</span></span> 

- <span data-ttu-id="beaa9-116">**Um grande número de pedidos de um ID de API por Inquilino Parceiro:** para algumas APIs do Partner Center, o estrangulamento é determinado pelo ID do Inquilino Parceiro, demasiadas chamadas para essas APIs no mesmo ID do Inquilino Parceiro resultarão em exceder o limiar de estrangulamento.</span><span class="sxs-lookup"><span data-stu-id="beaa9-116">**A large number of requests for an API per Partner Tenant ID**: for some Partner Center APIs, throttling is determined by Partner Tenant ID, too many calls to those APIs on the same Partner Tenant ID will result in exceeding the throttling threshold.</span></span>  

- <span data-ttu-id="beaa9-117">**Um grande número de pedidos de ID de API por Inquilino Sócio ID por ID do Cliente Inquilino:** para outras APIs, o estrangulamento é determinado pela combinação ID/Customer Tenant ID do Inquilino Sócio; nesses casos, fazer demasiadas chamadas contra o mesmo ID do inquilino do cliente resultará em estrangulamento - enquanto as chamadas contra outros clientes podem ter sucesso.</span><span class="sxs-lookup"><span data-stu-id="beaa9-117">**A large number of requests for an API per Partner Tenant ID per Customer Tenant ID**: for other APIs, throttling is determined by Partner Tenant ID/Customer Tenant ID combination; in those cases, making too many calls against the same customer tenant ID will result in throttling - while calls against other customers may succeed.</span></span>

## <a name="best-practices-to-avoid-throttling"></a><span data-ttu-id="beaa9-118">Melhores práticas para evitar estrangulamentos</span><span class="sxs-lookup"><span data-stu-id="beaa9-118">Best practices to avoid throttling</span></span> 
 
<span data-ttu-id="beaa9-119">Práticas de programação como a votação contínua de um recurso para verificar atualizações e digitalização regular de recolha de recursos para verificar recursos novos ou eliminados são mais propensos a conduzir a estrangulamentos e irão degradar o desempenho global.</span><span class="sxs-lookup"><span data-stu-id="beaa9-119">Programming practices such as continuously polling a resource to check for updates and regularly scanning resource collections to check for new or deleted resources are more likely to lead to throttling and will degrade overall performance.</span></span> <span data-ttu-id="beaa9-120">As chamadas simultâneas da API podem levar a um elevado número de pedidos por tempo unitário, o que também fará com que os pedidos sejam estrangulados.</span><span class="sxs-lookup"><span data-stu-id="beaa9-120">Concurrent API calls may lead to high number of requests per unit time, which will also cause requests to be throttled.</span></span> <span data-ttu-id="beaa9-121">Em vez disso, deve alavancar o rastreio de alterações e alterar notificações.</span><span class="sxs-lookup"><span data-stu-id="beaa9-121">You should instead leverage change tracking and change notifications.</span></span> <span data-ttu-id="beaa9-122">Além disso, deverá ser capaz de aproveitar os registos de atividade para detetar alterações, consulte [os registos de atividade do Partner Center](get-a-record-of-partner-center-activity-by-user.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="beaa9-122">Additionally, you should be able to leverage activity logs for detecting changes, see [Partner Center activity logs](get-a-record-of-partner-center-activity-by-user.md) for more information.</span></span>  <span data-ttu-id="beaa9-123">Recomendamos vivamente aos parceiros que considerem a utilização do registo de atividade API para obter mais eficiência e evitar estrangulamentos.</span><span class="sxs-lookup"><span data-stu-id="beaa9-123">We highly recommend partners to consider using the activity log API for more efficiency and to avoid throttling.</span></span> <span data-ttu-id="beaa9-124">Veja também o exemplo da utilização de registos de atividades, abaixo.</span><span class="sxs-lookup"><span data-stu-id="beaa9-124">See also the example of using activity logs, below.</span></span>

## <a name="best-practices-to-handle-throttling"></a><span data-ttu-id="beaa9-125">Melhores práticas para lidar com o estrangulamento</span><span class="sxs-lookup"><span data-stu-id="beaa9-125">Best practices to handle throttling</span></span>

<span data-ttu-id="beaa9-126">Seguem-se as melhores práticas de manuseamento de estrangulamentos:</span><span class="sxs-lookup"><span data-stu-id="beaa9-126">The following are best practices for handling throttling:</span></span> 

- <span data-ttu-id="beaa9-127">Reduza o grau de paralelismo.</span><span class="sxs-lookup"><span data-stu-id="beaa9-127">Reduce the degree of parallelism.</span></span> 
- <span data-ttu-id="beaa9-128">Reduza a frequência das chamadas.</span><span class="sxs-lookup"><span data-stu-id="beaa9-128">Reduce the frequency of calls.</span></span> 
- <span data-ttu-id="beaa9-129">Evite recaídas imediatas porque todos os pedidos se acumulam contra os seus limites de utilização.</span><span class="sxs-lookup"><span data-stu-id="beaa9-129">Avoid immediate retries because all requests accrue against your usage limits.</span></span> 

<span data-ttu-id="beaa9-130">Ao implementar o processamento de erros, utilize o código de erro HTTP 429 para detetar limitação de largura de banda.</span><span class="sxs-lookup"><span data-stu-id="beaa9-130">When you implement error handling, use the HTTP error code 429 to detect throttling.</span></span> <span data-ttu-id="beaa9-131">A resposta falhada inclui o cabeçalho de resposta Retry-After.</span><span class="sxs-lookup"><span data-stu-id="beaa9-131">The failed response includes the Retry-After response header.</span></span> <span data-ttu-id="beaa9-132">Recuar os pedidos utilizando o atraso de Retry-after é a forma mais rápida de recuperar do estrangulamento.</span><span class="sxs-lookup"><span data-stu-id="beaa9-132">Backing off requests using the Retry-after delay is the fastest way to recover from throttling.</span></span> 

<span data-ttu-id="beaa9-133">Para utilizar o atraso de retry-after, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="beaa9-133">To use the Retry-after delay, do the following:</span></span> 

1. <span data-ttu-id="beaa9-134">Aguarde o número de segundos especificados no cabeçalho Retry-After.</span><span class="sxs-lookup"><span data-stu-id="beaa9-134">Wait the number of seconds specified in the Retry-After header.</span></span> 

2. <span data-ttu-id="beaa9-135">Recandidutar o pedido.</span><span class="sxs-lookup"><span data-stu-id="beaa9-135">Retry the request.</span></span>  

3. <span data-ttu-id="beaa9-136">Se o pedido falhar novamente com um código de erro 429, ainda está a ser estrangulado.</span><span class="sxs-lookup"><span data-stu-id="beaa9-136">If the request fails again with a 429 error code, you are still being throttled.</span></span> <span data-ttu-id="beaa9-137">Relemplificando com o backoff exponencial, use o Retry-After recomendado atrasar e voltar a tentar o pedido até que tenha sucesso.</span><span class="sxs-lookup"><span data-stu-id="beaa9-137">Retry with Exponential backoff, use the recommended Retry-After delay and retry the request until it succeeds.</span></span>

4. <span data-ttu-id="beaa9-138">Se estiver a utilizar o SDK, receberá uma exceção com o código de estado 429 quando o seu pedido estiver a ser acelerado.</span><span class="sxs-lookup"><span data-stu-id="beaa9-138">If you are using SDK you'll receive an exception with status code 429 when your request is being throttled.</span></span> <span data-ttu-id="beaa9-139">Utilize a propriedade RetryAfter na exceção e relemisse o pedido após o tempo decorrido.</span><span class="sxs-lookup"><span data-stu-id="beaa9-139">Use the RetryAfter property in the exception and retry the request after the time is elapsed.</span></span>


## <a name="apis-currently-impacted-by-throttling"></a><span data-ttu-id="beaa9-140">APIs atualmente impactados pelo estrangulamento</span><span class="sxs-lookup"><span data-stu-id="beaa9-140">APIs currently impacted by throttling</span></span>

<span data-ttu-id="beaa9-141">A longo prazo, todos os Parceiros Center API que chamem o ponto final de "api.partnercenter.microsoft.com/" serão estrangulados.</span><span class="sxs-lookup"><span data-stu-id="beaa9-141">In the long run, every single Partner Center API that calls the endpoint “api.partnercenter.microsoft.com/” will be throttled.</span></span> <span data-ttu-id="beaa9-142">Atualmente, os limites de estrangulamento só são aplicados nas poucas APIs listadas abaixo.</span><span class="sxs-lookup"><span data-stu-id="beaa9-142">Currently, the throttling limits are only enforced on the few APIs listed below.</span></span> <span data-ttu-id="beaa9-143">O Partner Center irá recolher a telemetria em cada uma das APIs e ajustará dinamicamente os limites de estrangulamento.</span><span class="sxs-lookup"><span data-stu-id="beaa9-143">Partner Center will be collecting the telemetry on each of the APIs and will dynamically adjust the throttling limits.</span></span> <span data-ttu-id="beaa9-144">A tabela que se segue lista as APIs onde o estrangulamento é atualmente aplicado.</span><span class="sxs-lookup"><span data-stu-id="beaa9-144">The following table lists the APIs where throttling is currently enforced.</span></span>  


|<span data-ttu-id="beaa9-145">**Operação**</span><span class="sxs-lookup"><span data-stu-id="beaa9-145">**Operation**</span></span>| <span data-ttu-id="beaa9-146">**Documentação do Centro de Parceiros**</span><span class="sxs-lookup"><span data-stu-id="beaa9-146">**Partner Center documentation**</span></span>|       
|------------------------|----------------------------|
|<span data-ttu-id="beaa9-147">{baseURL}/v1/clientes/{customer_id}/encomendas</span><span class="sxs-lookup"><span data-stu-id="beaa9-147">{baseURL}/v1/customers/{customer_id}/orders</span></span>|[<span data-ttu-id="beaa9-148">criar uma ordem</span><span class="sxs-lookup"><span data-stu-id="beaa9-148">create an order</span></span>](create-an-order.md)|
|<span data-ttu-id="beaa9-149">{baseURL}/v1/customers/{customer-tenant-id}/subscrições/{id-for-subscription}/upgrades</span><span class="sxs-lookup"><span data-stu-id="beaa9-149">{baseURL}/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription}/upgrades</span></span>|[<span data-ttu-id="beaa9-150">transição de uma subscrição</span><span class="sxs-lookup"><span data-stu-id="beaa9-150">transition a subscription</span></span>](transition-a-subscription.md)|
|<span data-ttu-id="beaa9-151">{baseURL}/v1/customers/{customer-tenant-id}/orders/{order-id}</span><span class="sxs-lookup"><span data-stu-id="beaa9-151">{baseURL}/v1/customers/{customer-tenant-id}/orders/{order-id}</span></span>|[<span data-ttu-id="beaa9-152">comprar um addon a uma subscrição</span><span class="sxs-lookup"><span data-stu-id="beaa9-152">purchase an addon to a subscription</span></span>](purchase-an-add-on-to-a-subscription.md)|
|<span data-ttu-id="beaa9-153">{baseURL}/v1/customers/{customer-id}/carts/{cart-id}</span><span class="sxs-lookup"><span data-stu-id="beaa9-153">{baseURL}/v1/customers/{customer-id}/carts/{cart-id}</span></span>|[<span data-ttu-id="beaa9-154">criar um carrinho</span><span class="sxs-lookup"><span data-stu-id="beaa9-154">create a cart</span></span>](create-a-cart.md)|
|<span data-ttu-id="beaa9-155">{baseURL}/v1/customers/{customer-id}/carts/{cart-id}/check-out</span><span class="sxs-lookup"><span data-stu-id="beaa9-155">{baseURL}/v1/customers/{customer-id}/carts/{cart-id}/checkout</span></span>|[<span data-ttu-id="beaa9-156">checkout um carrinho</span><span class="sxs-lookup"><span data-stu-id="beaa9-156">checkout a cart</span></span>](checkout-a-cart.md)|
|<span data-ttu-id="beaa9-157">{baseURL}/v1/customers/{customer-id}/carts/{cart-id}</span><span class="sxs-lookup"><span data-stu-id="beaa9-157">{baseURL}/v1/customers/{customer-id}/carts/{cart-id}</span></span>|[<span data-ttu-id="beaa9-158">atualizar um carrinho</span><span class="sxs-lookup"><span data-stu-id="beaa9-158">update a cart</span></span>](update-a-cart.md)|
|<span data-ttu-id="beaa9-159">{baseURL}/v1/customers/{customer-id}/subscrições/{subscription-id}/registrations</span><span class="sxs-lookup"><span data-stu-id="beaa9-159">{baseURL}/v1/customers/{customer-id}/subscriptions/{subscription-id}/registrations</span></span>|[<span data-ttu-id="beaa9-160">registar uma subscrição</span><span class="sxs-lookup"><span data-stu-id="beaa9-160">register a subscription</span></span>](register-a-subscription.md)|
|<span data-ttu-id="beaa9-161">{baseURL}/v1/productupgrads</span><span class="sxs-lookup"><span data-stu-id="beaa9-161">{baseURL}/v1/productupgrades</span></span>|[<span data-ttu-id="beaa9-162">criar entidade de atualização de produtos</span><span class="sxs-lookup"><span data-stu-id="beaa9-162">create product upgrade entity</span></span>](create-product-upgrade-entity.md)|
|<span data-ttu-id="beaa9-163">{baseURL}/v1/customers/{customer-id}/subscrições/{subscription-id}/conversões</span><span class="sxs-lookup"><span data-stu-id="beaa9-163">{baseURL}/v1/customers/{customer-id}/subscriptions/{subscription-id}/conversions</span></span> |[<span data-ttu-id="beaa9-164">converter uma subscrição experimental para pago</span><span class="sxs-lookup"><span data-stu-id="beaa9-164">convert a trial subscription to paid</span></span>](convert-a-trial-subscription-to-paid.md)|
|<span data-ttu-id="beaa9-165">{baseURL}/v1/clientes/{cliente-inquilino-id}</span><span class="sxs-lookup"><span data-stu-id="beaa9-165">{baseURL}/v1/customers/{customer-tenant-id}</span></span>|[<span data-ttu-id="beaa9-166">obter um cliente por id</span><span class="sxs-lookup"><span data-stu-id="beaa9-166">get a customer by id</span></span>](get-a-customer-by-id.md)|
|<span data-ttu-id="beaa9-167">{baseURL}/v1/produtoUpgrades/elegibilidade</span><span class="sxs-lookup"><span data-stu-id="beaa9-167">{baseURL}/v1/productUpgrades/eligibility</span></span>|[<span data-ttu-id="beaa9-168">obter elegibilidade para atualização de produto</span><span class="sxs-lookup"><span data-stu-id="beaa9-168">get eligibility for product upgrade</span></span>](get-eligibility-for-product-upgrade.md)|
|<span data-ttu-id="beaa9-169">{baseURL}/v1/customers/{customer-tenant-id}/subscrições/{id-for-subscription}</span><span class="sxs-lookup"><span data-stu-id="beaa9-169">{baseURL}/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription}</span></span> |[<span data-ttu-id="beaa9-170">gerir subscrição</span><span class="sxs-lookup"><span data-stu-id="beaa9-170">manage subscription</span></span>](manage-orders.md#manage-a-subscription)|


### <a name="error-code-response"></a><span data-ttu-id="beaa9-171">Resposta do código de erro:</span><span class="sxs-lookup"><span data-stu-id="beaa9-171">Error code response:</span></span>
```http
HTTP/1.1 429 Too Many Requests 

Content-Length: 84 

Content-Type: application/json 

Retry-After: 57 

Date: Tue, 21 Jul 2020 04:10:58 GMT 

{ "statusCode": 429, "message": "Rate limit is exceeded. Try again in 57 seconds." } 
```

## <a name="example-of-activity-log"></a><span data-ttu-id="beaa9-172">Exemplo de log de atividade</span><span class="sxs-lookup"><span data-stu-id="beaa9-172">Example of activity log</span></span>

<span data-ttu-id="beaa9-173">Para as melhores práticas na análise de alterações diárias, recomendamos que você questione o registo de auditoria para um dia específico.</span><span class="sxs-lookup"><span data-stu-id="beaa9-173">For best practice in analyzing daily changes, we recommend that you query audit record for a specific day.</span></span> 

<span data-ttu-id="beaa9-174">Na resposta, obterá um resultado com alterações ao tipo de funcionamento específico.</span><span class="sxs-lookup"><span data-stu-id="beaa9-174">In the response, you will get a result with changes to specific operation type.</span></span><span data-ttu-id="beaa9-175">Pode filtrar com base na operação que lhe interessa.</span><span class="sxs-lookup"><span data-stu-id="beaa9-175">  You can filter based on the operation you care about.</span></span> <span data-ttu-id="beaa9-176">Por exemplo, se estiver interessado num cliente recém-criado, pode olhar para a operaçãoType = "add_customer".</span><span class="sxs-lookup"><span data-stu-id="beaa9-176"> For example, if you are interested in a newly created customer, you can look at operationType = “add_customer”.</span></span>  

<span data-ttu-id="beaa9-177">A lista de operação/recursos pode ser encontrada em documentos abaixo da API.</span><span class="sxs-lookup"><span data-stu-id="beaa9-177">List of operationtype/resources can be found in below API docs.</span></span>  

- [<span data-ttu-id="beaa9-178">Recursos de auditoria</span><span class="sxs-lookup"><span data-stu-id="beaa9-178">Auditing resources</span></span>](auditing-resources.md)  

- [<span data-ttu-id="beaa9-179">Obtenha um registo de uma atividade do Partner Center por utilizador</span><span class="sxs-lookup"><span data-stu-id="beaa9-179">Get a record of a Partner Center activity by user</span></span>](get-a-record-of-partner-center-activity-by-user.md)  



### <a name="response-example"></a><span data-ttu-id="beaa9-180">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="beaa9-180">Response example</span></span>

<span data-ttu-id="beaa9-181">**Pedido**:</span><span class="sxs-lookup"><span data-stu-id="beaa9-181">**Request**:</span></span>  
```http
Http Get call:  https://api.partnercenter.microsoft.com/v1/auditrecords?startDate=2020-09-02&endDate=2020-09-02&size=50 

Authorization: Bearer <token> 

Accept: application/json 

MS-RequestId: 127facaa-e389-41f8-8bb7-1d1af99db893 

MS-CorrelationId: de9c2ccc-40dd-4186-9660-65b9b64c3d14 

X-Locale: en-US 

Host: api.partnercenter.microsoft.com 

Connection: Keep-Alive 
```

<span data-ttu-id="beaa9-182">**Resposta:**</span><span class="sxs-lookup"><span data-stu-id="beaa9-182">**Response**:</span></span>    
```http
{ 

    "totalCount": 17, 

    "items": [ 

        { 

            "id": "9daaeb1c-4195-4db5-9f1d-509eb70c8c2d_e905b566-4779-4e57-944c-7b1b5312705b_updatecustomeruserlicenses_637346859797753934", 

            "partnerId": "9daaeb1c-4195-4db5-9f1d-509eb70c8c2d", 

            "participants": [ 

                "9daaeb1c-4195-4db5-9f1d-509eb70c8c2d" 

            ], 

            "customerId": "e905b566-4779-4e57-944c-7b1b5312705b", 

            "userPrincipalName": "admin@testsw09.onmicrosoft.com", 

            "applicationId": "FulfillmentService", 

            "resourceType": "license", 

            "operationType": "update_customer_user_licenses", 

            "operationDate": "2020-09-02T23:26:19.7753934Z", 

            "operationStatus": "succeeded", 

            "customizedData": [ 

                { 

                    "key": "CustomerUserId", 

                    "value": "933808c7-b165-496c-a24e-1a4b7846fab4" 

                } 

            ], 

            "attributes": { 

                "objectType": "AuditRecord" 

            } 

        }, 

        { 

            "id": "9daaeb1c-4195-4db5-9f1d-509eb70c8c2d_86bddccf-9a53-40c6-907c-08067a3f8da7_ia80zlkxp6ewoqpp35pbqjlhqv9iigvz1_createorder_637346662909268372", 

            "partnerId": "9daaeb1c-4195-4db5-9f1d-509eb70c8c2d", 

            "participants": [ 

                "9daaeb1c-4195-4db5-9f1d-509eb70c8c2d" 

            ], 

            "customerId": "86bddccf-9a53-40c6-907c-08067a3f8da7", 

            "customerName": "CustomMetersStagingTest", 

            "userPrincipalName": "admin@testsw09.onmicrosoft.com", 

            "applicationId": "4990cffe-04e8-4e8b-808a-1175604b879f", 

            "resourceType": "order", 

            "resourceNewValue": "{\"Id\":\"Ia80ZLkXp6eWOqpp35pBQJLhqv9IiGVZ1\",\"AlternateId\":\"64144d300bde\",\"ReferenceCustomerId\":\"86bddccf-9a53-40c6-907c-08067a3f8da7\",\"BillingCycle\":\"monthly\",\"CurrencyCode\":\"USD\",\"CurrencySymbol\":\"$\",\"LineItems\":[{\"LineItemNumber\":0,\"ProvisioningContext\":null,\"OfferId\":\"DZH318Z0C964:0001:DZH318Z0BZDG\",\"SubscriptionId\":\"f428d44a-d08b-348b-579e-ce92a6362c7b\",\"ParentSubscriptionId\":null,\"TermDuration\":\"P1M\",\"TransactionType\":\"New\",\"FriendlyName\":\"SaaS custom meter offer - Bronze\",\"Quantity\":1,\"Pricing\":null,\"PartnerIdOnRecord\":null,\"RenewsTo\":null,\"Links\":{\"Product\":{\"Uri\":\"/products/DZH318Z0C964?country=US\",\"Method\":\"GET\",\"Body\":null,\"Headers\":[]},\"Sku\":{\"Uri\":\"/products/DZH318Z0C964/skus/0001?country=US\",\"Method\":\"GET\",\"Body\":null,\"Headers\":[]},\"Availability\":{\"Uri\":\"/products/DZH318Z0C964/skus/0001/availabilities/DZH318Z0BZDG?country=US\",\"Method\":\"GET\",\"Body\":null,\"Headers\":[]},\"ActivationLinks\":{\"Uri\":\"/customers/86bddccf-9a53-40c6-907c-08067a3f8da7/orders/Ia80ZLkXp6eWOqpp35pBQJLhqv9IiGVZ1/lineitems/0/activationlinks\",\"Method\":\"GET\",\"Body\":null,\"Headers\":[]}}}],\"CreationDate\":\"2020-09-02T17:58:01.7755853Z\",\"Status\":\"pending\",\"TransactionType\":\"UserPurchase\",\"Links\":{\"Self\":{\"Uri\":\"/customers/86bddccf-9a53-40c6-907c-08067a3f8da7/orders/Ia80ZLkXp6eWOqpp35pBQJLhqv9IiGVZ1\",\"Method\":\"GET\",\"Body\":null,\"Headers\":[]},\"ProvisioningStatus\":{\"Uri\":\"/customers/86bddccf-9a53-40c6-907c-08067a3f8da7/orders/Ia80ZLkXp6eWOqpp35pBQJLhqv9IiGVZ1/provisioningstatus\",\"Method\":\"GET\",\"Body\":null,\"Headers\":[]},\"PatchOperation\":{\"Uri\":\"/customers/86bddccf-9a53-40c6-907c-08067a3f8da7/orders/Ia80ZLkXp6eWOqpp35pBQJLhqv9IiGVZ1\",\"Method\":\"PATCH\",\"Body\":null,\"Headers\":[]}},\"Client\":{\"marketplaceCountry\":\"US\",\"deviceFamily\":\"UniversalStore-PartnerCenter\",\"name\":\"Partner Center Web\"},\"Attributes\":{\"ObjectType\":\"Order\"}}", 

            "operationType": "create_order", 

            "originalCorrelationId": "96514ebe-c1b2-4865-cb46-2c2d20a2e911", 

            "operationDate": "2020-09-02T17:58:10.9268372Z", 

            "operationStatus": "succeeded", 

            "customizedData": [ 

                { 

                    "key": "OrderId", 

                    "value": "Ia80ZLkXp6eWOqpp35pBQJLhqv9IiGVZ1" 

                }, 

                { 

                    "key": "AlternateId", 

                    "value": "64144d300bde" 

                }, 

                { 

                    "key": "BillingCycle", 

                    "value": "Monthly" 

                }, 

                { 

                    "key": "OfferId-0", 

                    "value": "DZH318Z0C964:0001:DZH318Z0BZDG" 

                }, 

                { 

                    "key": "SubscriptionId-0", 

                    "value": "f428d44a-d08b-348b-579e-ce92a6362c7b" 

                }, 

                { 

                    "key": "SubscriptionName-0", 

                    "value": "SaaS custom meter offer - Bronze" 

                }, 

                { 

                   "key": "Quantity-0", 

                    "value": "1" 

                }, 

                { 

                    "key": "PartnerOnRecord-0", 

                    "value": null 

                } 

            ], 

            "attributes": { 

                "objectType": "AuditRecord" 

            } 

        }, 

                           { 

            "id": "9daaeb1c-4195-4db5-9f1d-509eb70c8c2d_86bddccf-9a53-40c6-907c-08067a3f8da7_86bddccf-9a53-40c6-907c-08067a3f8da7_addcustomer_637346648528069005", 

            "partnerId": "9daaeb1c-4195-4db5-9f1d-509eb70c8c2d", 

            "participants": [ 

                "9daaeb1c-4195-4db5-9f1d-509eb70c8c2d" 

            ], 

            "customerId": "86bddccf-9a53-40c6-907c-08067a3f8da7", 

            "customerName": "CustomMetersStagingTest", 

            "userPrincipalName": "admin@testsw09.onmicrosoft.com", 

            "applicationId": "4990cffe-04e8-4e8b-808a-1175604b879f", 

            "resourceType": "customer", 

            "resourceNewValue": "{\"Id\":\"86bddccf-9a53-40c6-907c-08067a3f8da7\",\"CommerceId\":\"9dd78b4f-f98a-44b4-a2fa-2b82ac58d24c\",\"CompanyProfile\":{\"TenantId\":\"86bddccf-9a53-40c6-907c-08067a3f8da7\",\"Domain\":\"CustomMetersStagingTest.onmicrosoft.com\",\"CompanyName\":\"CustomMetersStagingTest\",\"Address\":null,\"Email\":null,\"OrganizationRegistrationNumber\":null,\"Links\":{\"Self\":{\"Uri\":\"/customers/86bddccf-9a53-40c6-907c-08067a3f8da7/profiles/company\",\"Method\":\"GET\",\"Body\":null,\"Headers\":[]}},\"Attributes\":{\"ObjectType\":\"CustomerCompanyProfile\"}},\"BillingProfile\":{\"Id\":\"4beafd7b-cdab-5bdc-52ed-02e16edf2e7a\",\"FirstName\":\"CustomMetersStagingTest\",\"LastName\":\"CustomMetersStagingTest\",\"Email\":\"CustomMetersStagingTest@CustomMetersStagingTest.com\",\"Culture\":\"en-US\",\"Language\":\"en\",\"CompanyName\":\"CustomMetersStagingTest\",\"DefaultAddress\":{\"Id\":null,\"Country\":\"US\",\"Region\":null,\"City\":\"Seattle\",\"State\":\"WA\",\"District\":null,\"AddressLine1\":\"CustomMetersStagingTest\",\"AddressLine2\":null,\"AddressLine3\":null,\"PostalCode\":\"98122\",\"FirstName\":\"CustomMetersStagingTest\",\"LastName\":\"CustomMetersStagingTest\",\"EmailAddress\":null,\"PhoneNumber\":null,\"MiddleName\":null},\"Attributes\":{\"Etag\":\"-2279334701316321663\",\"ObjectType\":\"CustomerBillingProfile\"}},\"RelationshipToPartner\":\"reseller\",\"AllowDelegatedAccess\":true,\"UserCredentials\":{\"userName\":\"admin\",\"password\":\"\"},\"AssociatedPartnerId\":null,\"CustomDomains\":null,\"Attributes\":{\"ObjectType\":\"Customer\"}}", 

            "operationType": "add_customer", 

            "originalCorrelationId": "7550d9ea-e64a-416f-e49b-3670c516cf69", 

            "operationDate": "2020-09-02T17:34:12.8069005Z", 

            "operationStatus": "succeeded", 

            "customizedData": [ 

                { 

                    "key": "PrimaryDomainName", 

                    "value": "CustomMetersStagingTest.onmicrosoft.com" 

                }, 

                { 

                    "key": "Relationship", 

                    "value": "Reseller" 

                } 

            ], 

            "attributes": { 

                "objectType": "AuditRecord" 

            } 

        }, 

                            

        ... 

    ], 

    "links": { 

        "self": { 

            "uri": "/auditrecords?startDate=2020-09-02&endDate=2020-09-02&size=50", 

            "method": "GET", 

            "headers": [] 

        } 

    }, 

    "attributes": { 

        "objectType": "Collection" 

    } 

} 
```
 

