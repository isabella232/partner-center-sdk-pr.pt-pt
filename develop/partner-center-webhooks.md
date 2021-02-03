---
title: Webhooks do Centro de Parceiros
description: Os webhooks permitem que os parceiros se registem para eventos de mudança de recursos.
ms.date: 04/10/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: cychua
ms.author: cychua
ms.openlocfilehash: 8225623ade7e922ac23ebf0ed9215686b0601244
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/22/2020
ms.locfileid: "97769224"
---
# <a name="partner-center-webhooks"></a><span data-ttu-id="e5862-103">Webhooks do Centro de Parceiros</span><span class="sxs-lookup"><span data-stu-id="e5862-103">Partner Center webhooks</span></span>

<span data-ttu-id="e5862-104">**Aplica-se a**</span><span class="sxs-lookup"><span data-stu-id="e5862-104">**Applies To**</span></span>

- <span data-ttu-id="e5862-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="e5862-105">Partner Center</span></span>
- <span data-ttu-id="e5862-106">Centro de Parceiros operado pela 21Vianet</span><span class="sxs-lookup"><span data-stu-id="e5862-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="e5862-107">Centro de Parceiros para Microsoft Cloud Germany</span><span class="sxs-lookup"><span data-stu-id="e5862-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="e5862-108">Centro de Parceiros do Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="e5862-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="e5862-109">As APIs do Partner Center Webhook permitem que os parceiros se registem para eventos de mudança de recursos.</span><span class="sxs-lookup"><span data-stu-id="e5862-109">The Partner Center Webhook APIs allow partners to register for resource change events.</span></span> <span data-ttu-id="e5862-110">Estes eventos são entregues sob a forma de POSTs HTTP para o URL registado do parceiro.</span><span class="sxs-lookup"><span data-stu-id="e5862-110">These events are delivered in the form of HTTP POSTs to the partner's registered URL.</span></span> <span data-ttu-id="e5862-111">Para receber um evento do Partner Center, os parceiros irão acolher uma chamada onde o Partner Center pode publicar o evento de mudança de recursos.</span><span class="sxs-lookup"><span data-stu-id="e5862-111">To receive an event from Partner Center, partners will host a callback where Partner Center can POST the resource change event.</span></span> <span data-ttu-id="e5862-112">O evento será assinado digitalmente para que o parceiro possa verificar se foi enviado do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="e5862-112">The event will be digitally signed so that the partner can verify that it was sent from Partner Center.</span></span>

<span data-ttu-id="e5862-113">Os parceiros podem selecionar a partir de eventos Webhook, como os seguintes exemplos, que são suportados pelo Partner Center.</span><span class="sxs-lookup"><span data-stu-id="e5862-113">Partners can select from Webhook events, like the following examples, that are supported by Partner Center.</span></span>

- <span data-ttu-id="e5862-114">**Evento de teste ("criado pelo teste")**</span><span class="sxs-lookup"><span data-stu-id="e5862-114">**Test Event ("test-created")**</span></span>

    <span data-ttu-id="e5862-115">Este evento permite-lhe auto-a bordo e testar o seu registo solicitando um evento de teste e, em seguida, rastreando o seu progresso.</span><span class="sxs-lookup"><span data-stu-id="e5862-115">This event allows you to self-onboard and test your registration by requesting a test event and then tracking its progress.</span></span> <span data-ttu-id="e5862-116">Pode ver as mensagens de falha que estão a ser recebidas da Microsoft enquanto tenta entregar o evento.</span><span class="sxs-lookup"><span data-stu-id="e5862-116">You can see the failure messages that are being received from Microsoft while trying to deliver the event.</span></span> <span data-ttu-id="e5862-117">Esta restrição aplica-se apenas a eventos "criados por testes".</span><span class="sxs-lookup"><span data-stu-id="e5862-117">This restriction only applies to "test-created" events.</span></span> <span data-ttu-id="e5862-118">Dados com mais de sete dias serão purgados.</span><span class="sxs-lookup"><span data-stu-id="e5862-118">Data older than seven days will be purged.</span></span>

- <span data-ttu-id="e5862-119">**Evento Atualizado de Subscrição ("updated por subscrição")**</span><span class="sxs-lookup"><span data-stu-id="e5862-119">**Subscription Updated Event ("subscription-updated")**</span></span>

    <span data-ttu-id="e5862-120">Este evento é levantado quando a subscrição muda.</span><span class="sxs-lookup"><span data-stu-id="e5862-120">This event is raised when the subscription changes.</span></span> <span data-ttu-id="e5862-121">Estes eventos serão gerados quando houver uma mudança interna para além de quando as alterações são feitas através da API do Centro Parceiro.</span><span class="sxs-lookup"><span data-stu-id="e5862-121">These events will be generated when there is an internal change in addition to when changes are made through the Partner Center API.</span></span>

    >[!NOTE]
    ><span data-ttu-id="e5862-122">Há um atraso de até 48 horas entre a hora em que uma subscrição muda e quando o evento Atualizado de Subscrição é ativado.</span><span class="sxs-lookup"><span data-stu-id="e5862-122">There is a delay of up to 48 hours between the time a subscription changes and when the Subscription Updated event is triggered.</span></span>

- <span data-ttu-id="e5862-123">**Evento Excededo limiar ("usagerecords-thresholdExceeded")**</span><span class="sxs-lookup"><span data-stu-id="e5862-123">**Threshold Exceeded Event ("usagerecords-thresholdExceeded")**</span></span>

    <span data-ttu-id="e5862-124">Este evento é aumentado quando a quantidade de utilização do Microsoft Azure para qualquer cliente excede o seu orçamento de gastos de utilização (o seu limiar).</span><span class="sxs-lookup"><span data-stu-id="e5862-124">This event is raised when the amount of Microsoft Azure usage for any customer exceeds their usage spending budget (their threshold).</span></span> <span data-ttu-id="e5862-125">Para obter mais informações, consulte [Desconfiem de um orçamento de gastos Azure para os seus clientes/parceiro-centro/set-an-azure-spend-budget-for-your-customers).</span><span class="sxs-lookup"><span data-stu-id="e5862-125">For more information, see  [Set an Azure spending budget for your customers/partner-center/set-an-azure-spending-budget-for-your-customers).</span></span>

- <span data-ttu-id="e5862-126">**Evento Criado de Referência ("Referenciação-criado")**</span><span class="sxs-lookup"><span data-stu-id="e5862-126">**Referral Created Event ("referral-created")**</span></span>

    <span data-ttu-id="e5862-127">Este evento é levantado quando a referência é criada.</span><span class="sxs-lookup"><span data-stu-id="e5862-127">This event is raised when the referral is created.</span></span>

- <span data-ttu-id="e5862-128">**Evento Atualizado de Referência ("referenciação atualizada")**</span><span class="sxs-lookup"><span data-stu-id="e5862-128">**Referral Updated Event ("referral-updated")**</span></span>

    <span data-ttu-id="e5862-129">Este evento é levantado quando a referência é atualizada.</span><span class="sxs-lookup"><span data-stu-id="e5862-129">This event is raised when the referral is updated.</span></span>

- <span data-ttu-id="e5862-130">**Evento pronto para faturas ("pronto para fatura")**</span><span class="sxs-lookup"><span data-stu-id="e5862-130">**Invoice Ready Event ("invoice-ready")**</span></span>

    <span data-ttu-id="e5862-131">Este evento é levantado quando a nova fatura estiver pronta.</span><span class="sxs-lookup"><span data-stu-id="e5862-131">This event is raised when the new invoice is ready.</span></span>

<span data-ttu-id="e5862-132">Os eventos do Future Webhook serão adicionados para recursos que mudam no sistema que o parceiro não controla, e serão feitas novas atualizações para obter esses eventos o mais perto possível do "tempo real".</span><span class="sxs-lookup"><span data-stu-id="e5862-132">Future Webhook events will be added for resources that change in the system that the partner isn't in control of, and further updates will be made to get those events as close to "real time" as possible.</span></span> <span data-ttu-id="e5862-133">O feedback dos Parceiros sobre quais os eventos que acrescentam valor ao seu negócio será útil para determinar que novos eventos adicionar.</span><span class="sxs-lookup"><span data-stu-id="e5862-133">Feedback from Partners on which events add value to their business will be useful in determining what new events to add.</span></span>

<span data-ttu-id="e5862-134">Para obter uma lista completa de eventos Webhook apoiados pelo Partner Center, consulte [os eventos webhook do Partner Center](partner-center-webhook-events.md).</span><span class="sxs-lookup"><span data-stu-id="e5862-134">For a complete list of Webhook events supported by Partner Center, see [Partner Center webhook events](partner-center-webhook-events.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e5862-135">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="e5862-135">Prerequisites</span></span>

- <span data-ttu-id="e5862-136">Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="e5862-136">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="e5862-137">Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.</span><span class="sxs-lookup"><span data-stu-id="e5862-137">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

## <a name="receiving-events-from-partner-center"></a><span data-ttu-id="e5862-138">Receber eventos do Partner Center</span><span class="sxs-lookup"><span data-stu-id="e5862-138">Receiving events from Partner Center</span></span>

<span data-ttu-id="e5862-139">Para receber eventos do Partner Center, deve expor um ponto final acessível ao público.</span><span class="sxs-lookup"><span data-stu-id="e5862-139">To receive events from Partner Center, you must expose a publicly accessible endpoint.</span></span> <span data-ttu-id="e5862-140">Como este ponto final está exposto, deve validar que a comunicação é do Centro de Parceiros.</span><span class="sxs-lookup"><span data-stu-id="e5862-140">Because this endpoint is exposed, you must validate that the communication is from Partner Center.</span></span> <span data-ttu-id="e5862-141">Todos os eventos Webhook que recebe são assinados digitalmente com um certificado que acorra ao Microsoft Root.</span><span class="sxs-lookup"><span data-stu-id="e5862-141">All Webhook events that you receive are digitally signed with a certificate that chains to the Microsoft Root.</span></span> <span data-ttu-id="e5862-142">Será também fornecido um link para o certificado utilizado para assinar o evento.</span><span class="sxs-lookup"><span data-stu-id="e5862-142">A link to the certificate used to sign the event will also be provided.</span></span> <span data-ttu-id="e5862-143">Isto permitirá que o certificado seja renovado sem que tenha de reimplantar ou reconfigurar o seu serviço.</span><span class="sxs-lookup"><span data-stu-id="e5862-143">This will allow the certificate to be renewed without you having to redeploy or reconfigure your service.</span></span> <span data-ttu-id="e5862-144">O Partner Center fará 10 tentativas para entregar o evento.</span><span class="sxs-lookup"><span data-stu-id="e5862-144">Partner Center will make 10 attempts to deliver the event.</span></span> <span data-ttu-id="e5862-145">Se o evento ainda não for entregue após 10 tentativas, será movido para uma fila offline e não serão feitas mais tentativas na entrega.</span><span class="sxs-lookup"><span data-stu-id="e5862-145">If the event is still not delivered after 10 attempts, it will be moved into an offline queue and no further attempts will be made at delivery.</span></span>

<span data-ttu-id="e5862-146">A amostra que se segue mostra um evento publicado no Partner Center.</span><span class="sxs-lookup"><span data-stu-id="e5862-146">The following sample shows an event posted from Partner Center.</span></span>

```http
POST /webhooks/callback
Content-Type: application/json
Authorization: Signature VOhcjRqA4f7u/4R29ohEzwRZibZdzfgG5/w4fHUnu8FHauBEVch8m2+5OgjLZRL33CIQpmqr2t0FsGF0UdmCR2OdY7rrAh/6QUW+u+jRUCV1s62M76jbVpTTGShmrANxnl8gz4LsbY260LAsDHufd6ab4oejerx1Ey9sFC+xwVTa+J4qGgeyIepeu4YCM0oB2RFS9rRB2F1s1OeAAPEhG7olp8B00Jss3PQrpLGOoAr5+fnQp8GOK8IdKF1/abUIyyvHxEjL76l7DVQN58pIJg4YC+pLs8pi6sTKvOdSVyCnjf+uYQWwmmWujSHfyU37j2Fzz16PJyWH41K8ZXJJkw==
X-MS-Certificate-Url: https://3psostorageacct.blob.core.windows.net/cert/pcnotifications-dispatch.microsoft.com.cer
X-MS-Signature-Algorithm: rsa-sha256
Host: api.partnercenter.microsoft.com
Accept-Encoding: gzip, deflate
Content-Length: 195

{
    "EventName": "test-created",
    "ResourceUri": "http://localhost:16722/v1/webhooks/registration/test",
    "ResourceName": "test",
    "AuditUri": null,
    "ResourceChangeUtcDate": "2017-11-16T16:19:06.3520276+00:00"
}
```

>[!NOTE]
><span data-ttu-id="e5862-147">O cabeçalho de autorização tem um esquema de "Assinatura".</span><span class="sxs-lookup"><span data-stu-id="e5862-147">The Authorization header has a scheme of "Signature".</span></span> <span data-ttu-id="e5862-148">Esta é uma assinatura codificada base64 do conteúdo.</span><span class="sxs-lookup"><span data-stu-id="e5862-148">This is a base64 encoded signature of the content.</span></span>

## <a name="how-to-authenticate-the-callback"></a><span data-ttu-id="e5862-149">Como autenticar o retorno</span><span class="sxs-lookup"><span data-stu-id="e5862-149">How to authenticate the callback</span></span>

<span data-ttu-id="e5862-150">Para autenticar o evento de retorno recebido do Partner Center, siga estes passos:</span><span class="sxs-lookup"><span data-stu-id="e5862-150">To authenticate the callback event received from Partner Center, follow these steps:</span></span>

1. <span data-ttu-id="e5862-151">Verifique se os cabeçalhos necessários estão presentes (Autorização, x-ms-certificate-url, x-ms-signature-algorithm).</span><span class="sxs-lookup"><span data-stu-id="e5862-151">Verify the required headers are present (Authorization, x-ms-certificate-url, x-ms-signature-algorithm).</span></span>

2. <span data-ttu-id="e5862-152">Faça o download do certificado utilizado para assinar o conteúdo (x-ms-certificate-url).</span><span class="sxs-lookup"><span data-stu-id="e5862-152">Download the certificate used to sign the content (x-ms-certificate-url).</span></span>

3. <span data-ttu-id="e5862-153">Verifique a cadeia de certificados.</span><span class="sxs-lookup"><span data-stu-id="e5862-153">Verify the Certificate Chain.</span></span>

4. <span data-ttu-id="e5862-154">Verifique a "Organização" do certificado.</span><span class="sxs-lookup"><span data-stu-id="e5862-154">Verify the "Organization" of the certificate.</span></span>

5. <span data-ttu-id="e5862-155">Leia o conteúdo com a codificação utf8 num tampão.</span><span class="sxs-lookup"><span data-stu-id="e5862-155">Read the content with UTF8 encoding into a buffer.</span></span>

6. <span data-ttu-id="e5862-156">Crie um RSA Crypto Provider.</span><span class="sxs-lookup"><span data-stu-id="e5862-156">Create an RSA Crypto Provider.</span></span>

7. <span data-ttu-id="e5862-157">Verifique os dados correspondem ao que foi assinado com o algoritmo de haxixe especificado (por exemplo, SHA256).</span><span class="sxs-lookup"><span data-stu-id="e5862-157">Verify the data matches what was signed with the specified hash algorithm (for example SHA256).</span></span>

8. <span data-ttu-id="e5862-158">Se a verificação for bem sucedida, processe a mensagem.</span><span class="sxs-lookup"><span data-stu-id="e5862-158">If the verification succeeds, process the message.</span></span>

> [!NOTE]
> <span data-ttu-id="e5862-159">Por predefinição, o token de assinatura será enviado num cabeçalho de autorização.</span><span class="sxs-lookup"><span data-stu-id="e5862-159">By default, the signature token will be sent in an Authorization header.</span></span> <span data-ttu-id="e5862-160">Se definir **SignatureTokenToMsSssignatureHeader** para ser verdadeiro no seu registo, o token de assinatura será enviado no cabeçalho de assinatura x-ms.</span><span class="sxs-lookup"><span data-stu-id="e5862-160">If you set **SignatureTokenToMsSignatureHeader** to true in your registration, the signature token will be sent in the x-ms-signature header instead.</span></span>

## <a name="event-model"></a><span data-ttu-id="e5862-161">Modelo de evento</span><span class="sxs-lookup"><span data-stu-id="e5862-161">Event model</span></span>

<span data-ttu-id="e5862-162">A tabela seguinte descreve as propriedades de um evento partner center.</span><span class="sxs-lookup"><span data-stu-id="e5862-162">The following table describes the properties of a Partner Center event.</span></span>

### <a name="properties"></a><span data-ttu-id="e5862-163">Propriedades</span><span class="sxs-lookup"><span data-stu-id="e5862-163">Properties</span></span>

| <span data-ttu-id="e5862-164">Nome</span><span class="sxs-lookup"><span data-stu-id="e5862-164">Name</span></span>                      | <span data-ttu-id="e5862-165">Descrição</span><span class="sxs-lookup"><span data-stu-id="e5862-165">Description</span></span>                                                                           |
|---------------------------|---------------------------------------------------------------------------------------|
| <span data-ttu-id="e5862-166">**EventName**</span><span class="sxs-lookup"><span data-stu-id="e5862-166">**EventName**</span></span>             | <span data-ttu-id="e5862-167">O nome do evento.</span><span class="sxs-lookup"><span data-stu-id="e5862-167">The name of the event.</span></span> <span data-ttu-id="e5862-168">No formulário {recurso}-{ação}.</span><span class="sxs-lookup"><span data-stu-id="e5862-168">In the form {resource}-{action}.</span></span> <span data-ttu-id="e5862-169">Por exemplo, "testado".</span><span class="sxs-lookup"><span data-stu-id="e5862-169">For example, "test-created".</span></span>  |
| <span data-ttu-id="e5862-170">**RecursosUri**</span><span class="sxs-lookup"><span data-stu-id="e5862-170">**ResourceUri**</span></span>           | <span data-ttu-id="e5862-171">O URI do recurso que mudou.</span><span class="sxs-lookup"><span data-stu-id="e5862-171">The URI of the resource that changed.</span></span>                                                 |
| <span data-ttu-id="e5862-172">**Nome de recursos**</span><span class="sxs-lookup"><span data-stu-id="e5862-172">**ResourceName**</span></span>          | <span data-ttu-id="e5862-173">O nome do recurso que mudou.</span><span class="sxs-lookup"><span data-stu-id="e5862-173">The name of the resource that changed.</span></span>                                                |
| <span data-ttu-id="e5862-174">**AuditUrl**</span><span class="sxs-lookup"><span data-stu-id="e5862-174">**AuditUrl**</span></span>              | <span data-ttu-id="e5862-175">Opcional.</span><span class="sxs-lookup"><span data-stu-id="e5862-175">Optional.</span></span> <span data-ttu-id="e5862-176">O URI do registo de auditoria.</span><span class="sxs-lookup"><span data-stu-id="e5862-176">The URI of the Audit record.</span></span>                                                |
| <span data-ttu-id="e5862-177">**ResourceChangeUtcDate**</span><span class="sxs-lookup"><span data-stu-id="e5862-177">**ResourceChangeUtcDate**</span></span> | <span data-ttu-id="e5862-178">A data e a hora, no formato UTC, quando ocorreu a alteração de recursos.</span><span class="sxs-lookup"><span data-stu-id="e5862-178">The date and time, in UTC format, when the resource change occurred.</span></span>                  |

### <a name="sample"></a><span data-ttu-id="e5862-179">Sample</span><span class="sxs-lookup"><span data-stu-id="e5862-179">Sample</span></span>

<span data-ttu-id="e5862-180">A amostra que se segue mostra a estrutura de um evento do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="e5862-180">The following sample shows the structure of a Partner Center event.</span></span>

```http
{
    "EventName": "test-created",
    "ResourceUri": "http://api.partnercenter.microsoft.com/webhooks/v1/registration/validationEvents/c0bfd694-3075-4ec5-9a3c-733d3a890a1f",
    "ResourceName": "test",
    "AuditUri": null,
    "ResourceChangeUtcDate": "2017-11-16T16:19:06.3520276+00:00"
}
```

## <a name="webhook-apis"></a><span data-ttu-id="e5862-181">Webhook APIs</span><span class="sxs-lookup"><span data-stu-id="e5862-181">Webhook APIs</span></span>

### <a name="authentication"></a><span data-ttu-id="e5862-182">Autenticação</span><span class="sxs-lookup"><span data-stu-id="e5862-182">Authentication</span></span>

<span data-ttu-id="e5862-183">Todas as chamadas para as APIs webhook são autenticadas usando o token do portador no cabeçalho de autorização.</span><span class="sxs-lookup"><span data-stu-id="e5862-183">All calls to the Webhook APIs are authenticated using the Bearer token in the Authorization Header.</span></span> <span data-ttu-id="e5862-184">Adquira um token de acesso ao `https://api.partnercenter.microsoft.com` acesso.</span><span class="sxs-lookup"><span data-stu-id="e5862-184">Acquire an access token to access `https://api.partnercenter.microsoft.com`.</span></span> <span data-ttu-id="e5862-185">Este token é o mesmo símbolo que é usado para aceder ao resto das APIs do Centro De Parceiros.</span><span class="sxs-lookup"><span data-stu-id="e5862-185">This token is the same token that is used to access the rest of the Partner Center APIs.</span></span>

### <a name="get-a-list-of-events"></a><span data-ttu-id="e5862-186">Obtenha uma lista de eventos</span><span class="sxs-lookup"><span data-stu-id="e5862-186">Get a list of events</span></span>

<span data-ttu-id="e5862-187">Devolve uma lista dos eventos que são atualmente suportados pelas APIs do Webhook.</span><span class="sxs-lookup"><span data-stu-id="e5862-187">Returns a list of the events that are currently supported by the Webhook APIs.</span></span>

### <a name="resource-url"></a><span data-ttu-id="e5862-188">URL do recurso</span><span class="sxs-lookup"><span data-stu-id="e5862-188">Resource URL</span></span>

`https://api.partnercenter.microsoft.com/webhooks/v1/registration/events`

### <a name="request-example"></a><span data-ttu-id="e5862-189">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="e5862-189">Request example</span></span>

```http
GET /webhooks/v1/registration/events
content-type: application/json
authorization: Bearer eyJ0e.......
accept: */*
host: api.partnercenter.microsoft.com
```

### <a name="response-example"></a><span data-ttu-id="e5862-190">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="e5862-190">Response example</span></span>

```http
HTTP/1.1 200
Status: 200
Content-Length: 183
Content-Type: application/json; charset=utf-8
Content-Encoding: gzip
Vary: Accept-Encoding
MS-CorrelationId: c0bcf3a3-46e9-48fd-8e05-f674b8fd5d66
MS-RequestId: 79419bbb-06ee-48da-8221-e09480537dfc
X-Locale: en-US

[ "subscription-updated", "test-created", "usagerecords-thresholdExceeded" ]
```

### <a name="register-to-receive-events"></a><span data-ttu-id="e5862-191">Registe-se para receber eventos</span><span class="sxs-lookup"><span data-stu-id="e5862-191">Register to receive events</span></span>

<span data-ttu-id="e5862-192">Regista um inquilino para receber os eventos especificados.</span><span class="sxs-lookup"><span data-stu-id="e5862-192">Registers a tenant to receive the specified events.</span></span>

#### <a name="resource-url"></a><span data-ttu-id="e5862-193">URL do recurso</span><span class="sxs-lookup"><span data-stu-id="e5862-193">Resource URL</span></span>

`https://api.partnercenter.microsoft.com/webhooks/v1/registration`

### <a name="request-example"></a><span data-ttu-id="e5862-194">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="e5862-194">Request example</span></span>

```http
POST /webhooks/v1/registration
Content-Type: application/json
Authorization: Bearer eyJ0e.....
Accept: */*
Host: api.partnercenter.microsoft.com
Accept-Encoding: gzip, deflate
Content-Length: 219

{
    "WebhookUrl": "{{YourCallbackUrl}}",
    "WebhookEvents": ["subscription-updated", "test-created"]
}
```

### <a name="response-example"></a><span data-ttu-id="e5862-195">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="e5862-195">Response example</span></span>

```http
HTTP/1.1 200
Status: 200
Content-Length: 346
Content-Type: application/json; charset=utf-8
content-encoding: gzip
Vary: Accept-Encoding
MS-CorrelationId: 718f2336-8b56-4f42-93ac-54896047c59a
MS-RequestId: f04b1b5e-87b4-4d95-b087-d65fffec0bd2

{
    "SubscriberId": "e82cac64-dc67-4cd3-849b-78b6127dd57d",
    "WebhookUrl": "{{YourCallbackUrl}}",
    "WebhookEvents": [ "subscription-updated", "test-created" ]
}
```

### <a name="view-a-registration"></a><span data-ttu-id="e5862-196">Ver um registo</span><span class="sxs-lookup"><span data-stu-id="e5862-196">View a registration</span></span>

<span data-ttu-id="e5862-197">Devolve o registo do evento Webhooks a um inquilino.</span><span class="sxs-lookup"><span data-stu-id="e5862-197">Returns the Webhooks event registration for a tenant.</span></span>

#### <a name="resource-url"></a><span data-ttu-id="e5862-198">URL do recurso</span><span class="sxs-lookup"><span data-stu-id="e5862-198">Resource URL</span></span>

`https://api.partnercenter.microsoft.com/webhooks/v1/registration`

### <a name="request-example"></a><span data-ttu-id="e5862-199">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="e5862-199">Request example</span></span>

```http
GET /webhooks/v1/registration
Content-Type: application/json
Authorization: Bearer ...
Accept: */*
Host: api.partnercenter.microsoft.com
Accept-Encoding: gzip, deflate
```

### <a name="response-example"></a><span data-ttu-id="e5862-200">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="e5862-200">Response example</span></span>

```http
HTTP/1.1 200
Status: 200
Content-Length: 341
Content-Type: application/json; charset=utf-8
Content-Encoding: gzip
Vary: Accept-Encoding
MS-CorrelationId: c3b88ab0-b7bc-48d6-8c55-4ae6200f490a
MS-RequestId: ca30367d-4b24-4516-af08-74bba6dc6657
X-Locale: en-US

{
    "WebhookUrl": "{{YourCallbackUrl}}",
    "WebhookEvents": ["subscription-updated", "test-created"]
}
```

### <a name="update-an-event-registration"></a><span data-ttu-id="e5862-201">Atualizar um registo de eventos</span><span class="sxs-lookup"><span data-stu-id="e5862-201">Update an event registration</span></span>

<span data-ttu-id="e5862-202">Atualiza um registo de eventos existente.</span><span class="sxs-lookup"><span data-stu-id="e5862-202">Updates an existing event registration.</span></span>

#### <a name="resource-url"></a><span data-ttu-id="e5862-203">URL do recurso</span><span class="sxs-lookup"><span data-stu-id="e5862-203">Resource URL</span></span>

`https://api.partnercenter.microsoft.com/webhooks/v1/registration`

### <a name="request-example"></a><span data-ttu-id="e5862-204">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="e5862-204">Request example</span></span>

```http
PUT /webhooks/v1/registration
Content-Type: application/json
Authorization: Bearer eyJ0eXAiOR...
Accept: */*
Host: api.partnercenter.microsoft.com
Accept-Encoding: gzip, deflate
Content-Length: 258

{
    "WebhookUrl": "{{YourCallbackUrl}}",
    "WebhookEvents": ["subscription-updated", "test-created"]
}
```

### <a name="response-example"></a><span data-ttu-id="e5862-205">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="e5862-205">Response example</span></span>

```http
HTTP/1.1 200
Status: 200
Content-Length: 346
Content-Type: application/json; charset=utf-8
content-encoding: gzip
Vary: Accept-Encoding
MS-CorrelationId: 718f2336-8b56-4f42-93ac-54896047c59a
MS-RequestId: f04b1b5e-87b4-4d95-b087-d65fffec0bd2

{
    "SubscriberId": "e82cac64-dc67-4cd3-849b-78b6127dd57d",
    "WebhookUrl": "{{YourCallbackUrl}}",
    "WebhookEvents": [ "subscription-updated", "test-created" ]
}
```

### <a name="send-a-test-event-to-validate-your-registration"></a><span data-ttu-id="e5862-206">Envie um evento de teste para validar o seu registo</span><span class="sxs-lookup"><span data-stu-id="e5862-206">Send a test event to validate your registration</span></span>

<span data-ttu-id="e5862-207">Gera um evento de teste para validar o registo webhooks.</span><span class="sxs-lookup"><span data-stu-id="e5862-207">Generates a test event to validate the Webhooks registration.</span></span> <span data-ttu-id="e5862-208">Este teste destina-se a validar que pode receber eventos do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="e5862-208">This test is intended to validate that you can receive events from Partner Center.</span></span> <span data-ttu-id="e5862-209">Os dados para estes eventos serão eliminados sete dias após a criação do evento inicial.</span><span class="sxs-lookup"><span data-stu-id="e5862-209">Data for these events will be deleted seven days after the initial event is created.</span></span> <span data-ttu-id="e5862-210">Tem de estar registado para o evento "test-created", utilizando a API de registo, antes de enviar um evento de validação.</span><span class="sxs-lookup"><span data-stu-id="e5862-210">You must be registered for the "test-created" event, using the registration API, before sending a validation event.</span></span>

>[!NOTE]
><span data-ttu-id="e5862-211">Existe um limite de aceleração de 2 pedidos por minuto ao publicar um evento de validação.</span><span class="sxs-lookup"><span data-stu-id="e5862-211">There is a throttle limit of 2 requests per minute when posting a validation event.</span></span>

#### <a name="resource-url"></a><span data-ttu-id="e5862-212">URL do recurso</span><span class="sxs-lookup"><span data-stu-id="e5862-212">Resource URL</span></span>

`https://api.partnercenter.microsoft.com/webhooks/v1/registration/validationEvents`

### <a name="request-example"></a><span data-ttu-id="e5862-213">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="e5862-213">Request example</span></span>

```http
POST /webhooks/v1/registration/validationEvents
MS-CorrelationId: 3ef0202b-9d00-4f75-9cff-15420f7612b3
Authorization: Bearer ...
Accept: */*
Host: api.partnercenter.microsoft.com
Accept-Encoding: gzip, deflate
Content-Length:
```

### <a name="response-example"></a><span data-ttu-id="e5862-214">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="e5862-214">Response example</span></span>

```http
HTTP/1.1 200
Status: 200
Content-Length: 181
Content-Type: application/json; charset=utf-8
Content-Encoding: gzip
Vary: Accept-Encoding
MS-CorrelationId: 04af2aea-d413-42db-824e-f328001484d1
MS-RequestId: 2f498d5a-a6ab-468f-98d8-93c96da09051
X-Locale: en-US

{ "correlationId": "04af2aea-d413-42db-824e-f328001484d1" }
```

### <a name="verify-that-the-event-was-delivered"></a><span data-ttu-id="e5862-215">Verifique se o evento foi entregue</span><span class="sxs-lookup"><span data-stu-id="e5862-215">Verify that the event was delivered</span></span>

<span data-ttu-id="e5862-216">Devolve o estado atual do evento de validação.</span><span class="sxs-lookup"><span data-stu-id="e5862-216">Returns the current state of the validation event.</span></span> <span data-ttu-id="e5862-217">Esta verificação pode ser útil para resolver problemas de entrega de eventos.</span><span class="sxs-lookup"><span data-stu-id="e5862-217">This verification can be helpful for troubleshooting event delivery issues.</span></span> <span data-ttu-id="e5862-218">A Resposta contém um resultado para cada tentativa que é feita para entregar o evento.</span><span class="sxs-lookup"><span data-stu-id="e5862-218">The Response contains a result for each attempt that is made to deliver the event.</span></span>

#### <a name="resource-url"></a><span data-ttu-id="e5862-219">URL do recurso</span><span class="sxs-lookup"><span data-stu-id="e5862-219">Resource URL</span></span>

`https://api.partnercenter.microsoft.com/webhooks/v1/registration/validationEvents/{correlationId}`

### <a name="request-example"></a><span data-ttu-id="e5862-220">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="e5862-220">Request example</span></span>

```http
GET /webhooks/v1/registration/validationEvents/04af2aea-d413-42db-824e-f328001484d1
MS-CorrelationId: 3ef0202b-9d00-4f75-9cff-15420f7612b3
Authorization: Bearer ...
Accept: */*
Host: api.partnercenter.microsoft.com
Accept-Encoding: gzip, deflate
```

### <a name="response-example"></a><span data-ttu-id="e5862-221">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="e5862-221">Response example</span></span>

```http
HTTP/1.1 200
Status: 200
Content-Length: 469
Content-Type: application/json; charset=utf-8
Content-Encoding: gzip
Vary: Accept-Encoding
MS-CorrelationId: 497e0a23-9498-4d6c-bd6a-bc4d6d0054e7
MS-RequestId: 0843bdb2-113a-4926-a51c-284aa01d722e
X-Locale: en-US

{
    "correlationId": "04af2aea-d413-42db-824e-f328001484d1",
    "partnerId": "00234d9d-8c2d-4ff5-8c18-39f8afc6f7f3",
    "status": "completed",
    "callbackUrl": "{{YourCallbackUrl}}",
    "results": [{
        "responseCode": "OK",
        "responseMessage": "",
        "systemError": false,
        "dateTimeUtc": "2017-12-08T21:39:48.2386997"
    }]
}
```

## <a name="example-for-signature-validation"></a><span data-ttu-id="e5862-222">Exemplo para Validação de Assinaturas</span><span class="sxs-lookup"><span data-stu-id="e5862-222">Example for Signature Validation</span></span>

### <a name="sample-callback-controller-signature-aspnet"></a><span data-ttu-id="e5862-223">Assinatura do controlador de chamada de amostra (ASP.NET)</span><span class="sxs-lookup"><span data-stu-id="e5862-223">Sample Callback Controller signature (ASP.NET)</span></span>

``` csharp
[AuthorizeSignature]
[Route("webhooks/callback")]
public IHttpActionResult Post(PartnerResourceChangeCallBack callback)
```

### <a name="signature-validation"></a><span data-ttu-id="e5862-224">Validação de assinaturas</span><span class="sxs-lookup"><span data-stu-id="e5862-224">Signature Validation</span></span>

<span data-ttu-id="e5862-225">O exemplo a seguir mostra como adicionar um Atributo de Autorização ao controlador que está a receber chamadas de eventos webhook.</span><span class="sxs-lookup"><span data-stu-id="e5862-225">The following example shows how to add an Authorization Attribute to the controller that is receiving callbacks from Webhook events.</span></span>

``` csharp
namespace Webhooks.Security
{
    using System;
    using System.Collections.Generic;
    using System.IO;
    using System.Linq;
    using System.Net;
    using System.Net.Http;
    using System.Net.Http.Headers;
    using System.Security.Cryptography;
    using System.Security.Cryptography.X509Certificates;
    using System.Text;
    using System.Threading;
    using System.Threading.Tasks;
    using System.Web.Http;
    using System.Web.Http.Controllers;
    using Microsoft.Partner.Logging;

    /// <summary>
    /// Signature based Authorization
    /// </summary>
    public class AuthorizeSignatureAttribute : AuthorizeAttribute
    {
        private const string MsSignatureHeader = "x-ms-signature";
        private const string CertificateUrlHeader = "x-ms-certificate-url";
        private const string SignatureAlgorithmHeader = "x-ms-signature-algorithm";
        private const string MicrosoftCorporationIssuer = "O=Microsoft Corporation";
        private const string SignatureScheme = "Signature";

        /// <inheritdoc/>
        public override async Task OnAuthorizationAsync(HttpActionContext actionContext, CancellationToken cancellationToken)
        {
            ValidateAuthorizationHeaders(actionContext.Request);

            await VerifySignature(actionContext.Request);
        }

        private static async Task<string> GetContentAsync(HttpRequestMessage request)
        {
            // By default the stream can only be read once and we need to read it here so that we can hash the body to validate the signature from microsoft.
            // Load into a buffer, so that the stream can be accessed here and in the api when it binds the content to the expected model type.
            await request.Content.LoadIntoBufferAsync();

            var s = await request.Content.ReadAsStreamAsync();
            var reader = new StreamReader(s);
            var body = await reader.ReadToEndAsync();

            // set the stream position back to the beginning
            if (s.CanSeek)
            {
                s.Seek(0, SeekOrigin.Begin);
            }

            return body;
        }

        private static void ValidateAuthorizationHeaders(HttpRequestMessage request)
        {
            var authHeader = request.Headers.Authorization;
            if (string.IsNullOrWhiteSpace(authHeader?.Parameter) && string.IsNullOrWhiteSpace(GetHeaderValue(request.Headers, MsSignatureHeader)))
            {
                throw new HttpResponseException(request.CreateErrorResponse(HttpStatusCode.Unauthorized, "Authorization header missing."));
            }

            var signatureHeaderValue = GetHeaderValue(request.Headers, MsSignatureHeader);
            if (authHeader != null
                && !string.Equals(authHeader.Scheme, SignatureScheme, StringComparison.OrdinalIgnoreCase)
                && !string.IsNullOrWhiteSpace(signatureHeaderValue)
                && !signatureHeaderValue.StartsWith(SignatureScheme, StringComparison.OrdinalIgnoreCase))
            {
                throw new HttpResponseException(request.CreateErrorResponse(HttpStatusCode.Unauthorized, $"Authorization scheme needs to be '{SignatureScheme}'."));
            }

            if (string.IsNullOrWhiteSpace(GetHeaderValue(request.Headers, CertificateUrlHeader)))
            {
                throw new HttpResponseException(request.CreateErrorResponse(HttpStatusCode.BadRequest, $"Request header {CertificateUrlHeader} missing."));
            }

            if (string.IsNullOrWhiteSpace(GetHeaderValue(request.Headers, SignatureAlgorithmHeader)))
            {
                throw new HttpResponseException(request.CreateErrorResponse(HttpStatusCode.BadRequest, $"Request header {SignatureAlgorithmHeader} missing."));
            }
        }

        private static string GetHeaderValue(HttpHeaders headers, string key)
        {
            headers.TryGetValues(key, out var headerValues);

            return headerValues?.FirstOrDefault();
        }

        private static async Task VerifySignature(HttpRequestMessage request)
        {
            // Get signature value from either authorization header or x-ms-signature header.
            var base64Signature = request.Headers.Authorization?.Parameter ?? GetHeaderValue(request.Headers, MsSignatureHeader).Split(' ')[1];
            var signatureAlgorithm = GetHeaderValue(request.Headers, SignatureAlgorithmHeader);
            var certificateUrl = GetHeaderValue(request.Headers, CertificateUrlHeader);
            var certificate = await GetCertificate(certificateUrl);
            var content = await GetContentAsync(request);
            var alg = signatureAlgorithm.Split('-'); // for example RSA-SHA1
            var isValid = false;

            var logger = GetLoggerIfAvailable(request);

            // Validate the certificate
            VerifyCertificate(certificate, request, logger);

            if (alg.Length == 2 && alg[0].Equals("RSA", StringComparison.OrdinalIgnoreCase))
            {
                var signature = Convert.FromBase64String(base64Signature);
                var csp = (RSACryptoServiceProvider)certificate.PublicKey.Key;

                var encoding = new UTF8Encoding();
                var data = encoding.GetBytes(content);

                var hashAlgorithm = alg[1].ToUpper();

                isValid = csp.VerifyData(data, CryptoConfig.MapNameToOID(hashAlgorithm), signature);
            }

            if (!isValid)
            {
                // log that we were not able to validate the signature
                logger?.TrackTrace(
                    "Failed to validate signature for webhook callback",
                    new Dictionary<string, string> { { "base64Signature", base64Signature }, { "certificateUrl", certificateUrl }, { "signatureAlgorithm", signatureAlgorithm }, { "content", content } });

                throw new HttpResponseException(request.CreateErrorResponse(HttpStatusCode.Unauthorized, "Signature verification failed"));
            }
        }

        private static ILogger GetLoggerIfAvailable(HttpRequestMessage request)
        {
            return request.GetDependencyScope().GetService(typeof(ILogger)) as ILogger;
        }

        private static async Task<X509Certificate2> GetCertificate(string certificateUrl)
        {
            byte[] certBytes;
            using (var webClient = new WebClient())
            {
                certBytes = await webClient.DownloadDataTaskAsync(certificateUrl);
            }

            return new X509Certificate2(certBytes);
        }

        private static void VerifyCertificate(X509Certificate2 certificate, HttpRequestMessage request, ILogger logger)
        {
            if (!certificate.Verify())
            {
                logger?.TrackTrace("Failed to verify certificate for webhook callback.", new Dictionary<string, string> { { "Subject", certificate.Subject }, { "Issuer", certificate.Issuer } });

                throw new HttpResponseException(request.CreateErrorResponse(HttpStatusCode.Unauthorized, "Certificate verification failed."));
            }

            if (!certificate.Issuer.Contains(MicrosoftCorporationIssuer))
            {
                logger?.TrackTrace($"Certificate not issued by {MicrosoftCorporationIssuer}.", new Dictionary<string, string> { { "Issuer", certificate.Issuer } });

                throw new HttpResponseException(request.CreateErrorResponse(HttpStatusCode.Unauthorized, $"Certificate not issued by {MicrosoftCorporationIssuer}."));
            }
        }
    }
}
```
