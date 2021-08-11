---
title: Eliminar uma conta de cliente do sandbox de integração
description: Como eliminar uma conta de cliente da caixa de areia de integração Test in Production (Tip).
ms.date: 06/20/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 9b0fa05055f49100ac80f3bc6897b3fbd0a47e32a06806ecfdc8e386e31ae1b9
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/06/2021
ms.locfileid: "115995089"
---
# <a name="delete-a-customer-account-from-the-integration-sandbox"></a>Eliminar uma conta de cliente do sandbox de integração

**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government

Este artigo explica como quebrar a relação entre o parceiro e a conta do cliente e recuperar a quota de Testes em Produção (Dica) de integração de areia.

> [!IMPORTANT]
> Quando eliminar uma conta de cliente, todos os recursos associados a esse inquilino do cliente serão purgados.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.

- Um ID do cliente ( `customer-tenant-id` ). Se não souber a identificação do cliente, pode procurar no [painel](https://partner.microsoft.com/dashboard)do Partner Center. Selecione **CSP** no menu Partner Center, seguido de **Clientes**. Selecione o cliente da lista de clientes e, em seguida, selecione **Conta.** Na página conta do cliente, procure o **ID** da Microsoft na secção Informação da **Conta do Cliente.** O ID da Microsoft é o mesmo que o ID do cliente ( `customer-tenant-id` ).

- Todas as instâncias de compra de máquinas virtuais reservadas Azure e as ordens de compra de software devem ser canceladas antes de eliminar um cliente da caixa de areia de integração da Ponta.

## <a name="c"></a>C\#

Para eliminar um cliente da caixa de areia de integração da Ponta:

1. Passe as credenciais de conta De ponta para o método [**CreatePartnerOperations**](/dotnet/api/microsoft.store.partnercenter.partnerservice.instance) para obter uma interface [**IPartner**](/dotnet/api/microsoft.store.partnercenter.ipartner) para operações parceiras.

2. Utilize a interface de operações do parceiro para recuperar a recolha de direitos:

    1. Ligue para o método [**Clientes.ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) com o identificador de clientes para especificar o cliente.

    2. Ligue para a propriedade **Entitlements.**

    3. Ligue para o método **Get** or **GetAsync** para recuperar a coleção [**Entitlement.**](entitlement-resources.md)

3. Certifique-se de que todas as instâncias de compra de máquinas virtuais reservadas a Azure e as encomendas de compra de software para esse cliente estão canceladas. Para cada [**Direito**](entitlement-resources.md) na coleção:

    1. Use o [**direito. ReferenceOrder.Id**](entitlement-resources.md#referenceorder) obter uma cópia local da [Encomenda](order-resources.md#order) correspondente da recolha de encomendas do cliente.

    2. Desa estada a [**propriedade Order.Status**](order-resources.md#order) para "Cancelado".

    3. Utilize o método **Patch()** para atualizar a encomenda.

4. Cancele todas as encomendas. Por exemplo, a seguinte amostra de código utiliza um loop para sondar cada encomenda até que o seu estado seja "Cancelado".

    ``` csharp
    // IPartnerCredentials tipAccountCredentials;
    // Customer tenant Id to be deleted.
    // string customerTenantId;

    IPartner tipAccountPartnerOperations = PartnerService.Instance.CreatePartnerOperations(tipAccountCredentials);

    // Get all entitlements whose order must be canceled.
    ResourceCollection<Entitlement> entitlements = tipAccountPartnerOperations.Customers.ById(customerTenantId).Entitlements.Get();

    // Cancel all orders
    foreach (var entitlement in entitlements)
    {
        var order = tipAccountPartnerOperations.Customers.ById(customerTenantId).Orders.ById(entitlement.ReferenceOrder.Id).Get();
        order.Status = "Cancelled";
        order = tipAccountPartnerOperations.Customers.ById(customerTenantId).Orders.ById(order.Id).Patch(order);
    }

    // Keep polling until the status of all orders is "Cancelled".
    bool proceed = true;
    do
    {
        // Check if all the orders were canceled.
        foreach (var entitlement in entitlements)
        {
            var order = tipAccountPartnerOperations.Customers.ById(customerTenantId).Orders.ById(entitlement.ReferenceOrder.Id).Get();
            if (!order.Status.Equals("Cancelled", StringComparison.OrdinalIgnoreCase))
            {
                proceed = false;
            }
        }

        // Wait for a few seconds.
        Thread.Sleep(5000);
    }
    while (proceed == false);

    tipAccountPartnerOperations.Customers.ById(customerTenantId).Delete();
    ```

5. Certifique-se de que todas as encomendas são canceladas ligando para o método **Eliminar** para o cliente.

**Amostra**: [App de teste de consola](console-test-app.md). **Project**: Partner Center PartnerCenterSDK.FeaturesSamples **Class**: DeleteCustomerFromTipAccount.cs

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método     | URI do pedido                                                                            |
|------------|----------------------------------------------------------------------------------------|
| DELETE     | [*{baseURL}*](partner-center-rest-urls.md)/v1/clientes/{cliente-inquilino-id} HTTP/1.1 |

#### <a name="uri-parameter"></a>Parâmetro URI

Utilize o seguinte parâmetro de consulta para eliminar um cliente.

| Nome                   | Tipo     | Necessário | Descrição                                                                         |
|------------------------|----------|----------|-------------------------------------------------------------------------------------|
| cliente-inquilino-id     | GUID     | Y        | O valor é um design **de cliente-inquilino-inquilino** formatado guid que permite ao revendedor filtrar os resultados de um dado cliente que pertence ao revendedor. |

### <a name="request-headers"></a>Cabeçalhos do pedido

Para obter mais informações, consulte [os cabeçalhos Partner Center REST](headers.md).

### <a name="request-body"></a>Corpo do pedido

Nenhum.

### <a name="request-example"></a>Exemplo de pedido

```http
DELETE https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id> HTTP/1.1
Accept: application/json
MS-RequestId: 655890ba-4d2b-4d09-a95f-4ea1348686a5
MS-CorrelationId: 1438ea3d-b515-45c7-9ec1-27ee0cc8e6bd
Content-Length: 0
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, este método devolve uma resposta vazia.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte os [códigos de erro do Partner Center REST](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

```http
HTTP/1.1 204 No Content
Content-Length: 0
MS-CorrelationId: 1438ea3d-b515-45c7-9ec1-27ee0cc8e6bd
MS-RequestId: 655890ba-4d2b-4d09-a95f-4ea1348686a5
Date: Wed, 16 Mar 2016 00:43:02 GMT
```
