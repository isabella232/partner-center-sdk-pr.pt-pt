---
title: Documentação de orientação da limitação de largura de banda da API
description: Para os parceiros que chamam APIs do Partner Center, saiba quais as APIs que são impactadas pelo estrangulamento da Microsoft API e pelas melhores práticas para evitar ou lidar melhor com o estrangulamento.
ms.date: 04/14/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: vijvala
ms.author: vijvala
ms.openlocfilehash: 4eead16c5bb2b01f0fba85e30ea35fbcdae9d5a6682872eecfeeb9e47f43d324
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115993763"
---
# <a name="api-throttling-guidance-for-partners-calling-partner-center-apis"></a>API acelera orientação para parceiros que chamam APIs do Partner Center 

A Microsoft está a implementar o estrangulamento da API para permitir um desempenho mais consistente dentro de um período de tempo para os parceiros que chamam as APIs do Partner Center. O estrangulamento limita o número de pedidos a um serviço num período de tempo para evitar o uso excessivo de recursos. Enquanto o Partner Center é projetado para lidar com um grande volume de pedidos, se um número esmagador de pedidos ocorrer por poucos parceiros, o estrangulamento ajuda a manter o melhor desempenho e fiabilidade para todos os parceiros.  

Os limites de estrangulamento variam em função do cenário. Por exemplo, se estiver a executar um grande volume de escritas, a possibilidade de estrangulamento é maior do que se estiver apenas a executar leituras.

## <a name="what-happens-when-throttling-occurs"></a>O que acontece quando o estrangulamento ocorre? 

Quando um limiar de estrangulamento é ultrapassado, o Partner Center limita quaisquer pedidos adicionais desse cliente por um período de tempo. O comportamento de estrangulamento depende do tipo e do número de pedidos.   

### <a name="common-throttling-scenarios"></a>Cenários comuns de estrangulamento 

As causas mais comuns de estrangulamento dos clientes incluem: 

- **Um grande número de pedidos de um ID de API por Inquilino Parceiro:** para algumas APIs do Partner Center, o estrangulamento é determinado pelo ID do Inquilino Parceiro, demasiadas chamadas para essas APIs no mesmo ID do Inquilino Parceiro resultarão em exceder o limiar de estrangulamento.  

- **Um grande número de pedidos de ID de API por Inquilino Sócio ID por ID do Cliente Inquilino:** para outras APIs, o estrangulamento é determinado pela combinação ID/Customer Tenant ID do Inquilino Sócio; nesses casos, fazer demasiadas chamadas contra o mesmo ID do inquilino do cliente resultará em estrangulamento - enquanto as chamadas contra outros clientes podem ter sucesso.

## <a name="best-practices-to-avoid-throttling"></a>Melhores práticas para evitar estrangulamentos 
 
Práticas de programação como a votação contínua de um recurso para verificar atualizações e digitalização regular de recolha de recursos para verificar recursos novos ou eliminados são mais propensos a conduzir a estrangulamentos e irão degradar o desempenho global. As chamadas simultâneas da API podem levar a um elevado número de pedidos por tempo unitário, o que também fará com que os pedidos sejam estrangulados. Em vez disso, deve utilizar o rastreio de alterações e alterar notificações. Além disso, deverá ser capaz de utilizar registos de atividade para detetar alterações. Para obter mais informações, consulte [os registos de atividade do Partner Center](get-a-record-of-partner-center-activity-by-user.md).  Recomendamos vivamente aos parceiros que considerem a utilização do registo de atividade API para obter mais eficiência e evitar estrangulamentos. Veja também o exemplo da utilização de registos de atividades, abaixo.

## <a name="best-practices-to-handle-throttling"></a>Melhores práticas para lidar com o estrangulamento

Seguem-se as melhores práticas de manuseamento de estrangulamentos: 

- Reduza o grau de paralelismo. 
- Reduza a frequência das chamadas. 
- Evite recaídas imediatas porque todos os pedidos se acumulam contra os seus limites de utilização. 

Ao implementar o processamento de erros, utilize o código de erro HTTP 429 para detetar limitação de largura de banda. A resposta falhada inclui o cabeçalho de resposta Retry-After. Recuar os pedidos utilizando o atraso de Retry-after é a forma mais rápida de recuperar do estrangulamento. 

Para utilizar o atraso de retry-after, faça o seguinte: 

1. Aguarde o número de segundos especificados no cabeçalho Retry-After. 

2. Recandidutar o pedido.  

3. Se o pedido falhar novamente com um código de erro 429, ainda está a ser estrangulado. Relemplificando com o backoff exponencial, use o Retry-After recomendado atrasar e voltar a tentar o pedido até que tenha sucesso.

4. Se estiver a utilizar o SDK, receberá uma exceção com o código de estado 429 quando o seu pedido estiver a ser acelerado. Utilize a propriedade RetryAfter na exceção e relemisse o pedido após o tempo decorrido.


## <a name="apis-currently-impacted-by-throttling"></a>APIs atualmente impactados pelo estrangulamento

No final, todos os Parceiros API que chamarem o ponto final de "api.partnercenter.microsoft.com/" serão estrangulados. Atualmente, os limites de estrangulamento só são aplicados nas APIs listadas abaixo. O Partner Center irá recolher a telemetria em cada uma das APIs e ajustará dinamicamente os limites de estrangulamento. A tabela que se segue lista as APIs onde o estrangulamento é atualmente aplicado.  


|**Operação**| **Documentação do Centro de Parceiros**|
|------------------------|----------------------------|
|{baseURL}/v1/clientes/{customer_id}/encomendas|[criar uma ordem](create-an-order.md)|
|{baseURL}/v1/customers/{customer-tenant-id}/subscrições/{id-for-subscription}/upgrades|[transição de uma subscrição](transition-a-subscription.md)|
|{baseURL}/v1/customers/{customer-tenant-id}/orders/{order-id}|[comprar um addon a uma subscrição](purchase-an-add-on-to-a-subscription.md)|
|{baseURL}/v1/customers/{customer-id}/carts/{cart-id}|[criar um carrinho](create-a-cart.md)|
|{baseURL}/v1/customers/{customer-id}/carts/{cart-id}/check-out|[checkout um carrinho](checkout-a-cart.md)|
|{baseURL}/v1/customers/{customer-id}/carts/{cart-id}|[atualizar um carrinho](update-a-cart.md)|
|{baseURL}/v1/customers/{customer-id}/subscrições/{subscription-id}/registrations|[registar uma subscrição](register-a-subscription.md)|
|{baseURL}/v1/productupgrads|[criar entidade de atualização de produtos](create-product-upgrade-entity.md)|
|{baseURL}/v1/customers/{customer-id}/subscrições/{subscription-id}/conversões |[converter uma subscrição experimental para pago](convert-a-trial-subscription-to-paid.md)|
|{baseURL}/v1/clientes/{cliente-inquilino-id}|[obter um cliente por ID](get-a-customer-by-id.md)|
|{baseURL}/v1/produtoUpgrades/elegibilidade|[obter elegibilidade para atualização de produto](get-eligibility-for-product-upgrade.md)|
|{baseURL}/v1/customers/{customer-tenant-id}/subscrições/{id-for-subscription} |[gerir subscrição](manage-orders.md#manage-a-subscription)|
|{baseURL}/v1/clientes/{customer_id}/subscrições |[obter-all-of-a-customer-s-subscrições](get-all-of-a-customer-s-subscriptions.md)|
|{baseURL}/v1/customers/{customer_id}/subscrições/{subscription_id}|[Obter uma subscrição por ID](get-a-subscription-by-id.md)|
|{baseURL}/v1/clientes/{customer_id}/encomendas|[Receba todas as encomendas de clientes](get-all-of-a-customer-s-orders.md)|
|{baseURL}/v1/customers/{customer_id}/orders/{order_id}|[Obter encomenda por ID](get-an-order-by-id.md)|
|{baseURL}/v1/customers/{customer_id}/orders/{order_id}/provisioningstatus|[Obter o estado de aprovisionamento da subscrição](get-subscription-provisioning-status.md)|
|{baseURL}/v1/customers/{customer_id}/subscrições/{subscription_id}|[Gerir encomendas e gerir uma subscrição](manage-orders.md#manage-a-subscription)|
|{baseURL}/v1/customers/{customer_id}/subscrições/{subscription_id}/addons|[Obter uma lista de suplementos para uma subscrição](get-a-list-of-add-ons-for-a-subscription.md)|
|{baseURL}/v1/customers/{customer_id}/subscrições/{subscription_id}/azureEntitlements|[Obtenha uma lista de direitos Azure para uma subscrição](get-a-list-of-azure-entitlements-for-subscription.md)|
|{baseURL}/v1/customers/{customer_id}/subscrições/{subscription_id}/registrationstatus|[Obter o estado de registo da subscrição](get-subscription-registration-status.md)|
|{baseURL}/v1/clientes/{cliente-inquilino-id}/transfers|[Obtenha todas as transferências de um cliente](get-all-of-a-customer-s-transfers.md)|
|{baseURL}/v1/productUpgrades/{upgrade-id}/status|[Obter estado de atualização do produto](get-product-upgrade-status.md)|
|{baseURL}/v1/customers/{customer-id}/subscrições/{subscription-id}/conversões|[Obter uma lista de ofertas de conversão de avaliação](get-a-list-of-trial-conversion-offers.md)|


### <a name="error-code-response"></a>Resposta do código de erro:
```http
HTTP/1.1 429 Too Many Requests 

Content-Length: 84 

Content-Type: application/json 

Retry-After: 57 

Date: Tue, 21 Jul 2020 04:10:58 GMT 

{ "statusCode": 429, "message": "Rate limit is exceeded. Try again in 57 seconds." } 
```

## <a name="example-of-activity-log"></a>Exemplo de log de atividade

Para as melhores práticas na análise de alterações diárias, recomendamos que você questione o registo de auditoria para um dia específico. 

Na resposta, obterá um resultado com alterações ao tipo de funcionamento específico.Pode filtrar com base na operação que lhe interessa. Por exemplo, se estiver interessado num cliente recém-criado, pode olhar para a operaçãoType = "add_customer".  

A lista de operação/recursos pode ser encontrada em documentos abaixo da API.  

- [Recursos de auditoria](auditing-resources.md)  

- [Obtenha um registo de uma atividade do Partner Center por utilizador](get-a-record-of-partner-center-activity-by-user.md)  



### <a name="response-example"></a>Exemplo de resposta

**Pedido**:  
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

**Resposta:**    
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
 

