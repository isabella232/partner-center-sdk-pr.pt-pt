---
title: Webhooks do Centro de Parceiros
description: Os webhooks permitem que os parceiros se registem para eventos de mudança de recursos.
ms.date: 04/10/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: cychua
ms.author: cychua
ms.openlocfilehash: 74d5981436ba29ea4f6f93a5693ec6da82777eb4
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/06/2021
ms.locfileid: "111547755"
---
# <a name="partner-center-webhooks"></a>Webhooks do Centro de Parceiros

**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government

As APIs do Partner Center Webhook permitem que os parceiros se registem para eventos de mudança de recursos. Estes eventos são entregues sob a forma de POSTs HTTP para o URL registado do parceiro. Para receber um evento do Partner Center, os parceiros irão acolher uma chamada onde o Partner Center pode publicar o evento de mudança de recursos. O evento será assinado digitalmente para que o parceiro possa verificar se foi enviado do Partner Center.

Os parceiros podem selecionar a partir de eventos Webhook, como os seguintes exemplos, que são suportados pelo Partner Center.

- **Evento de teste ("criado pelo teste")**

    Este evento permite-lhe auto-a bordo e testar o seu registo solicitando um evento de teste e, em seguida, rastreando o seu progresso. Pode ver as mensagens de falha que estão a ser recebidas da Microsoft enquanto tenta entregar o evento. Esta restrição aplica-se apenas a eventos "criados por testes". Dados com mais de sete dias serão purgados.

- **Evento Atualizado de Subscrição ("updated por subscrição")**

    Este evento é levantado quando a subscrição muda. Estes eventos serão gerados quando houver uma mudança interna para além de quando as alterações são feitas através da API do Centro Parceiro.

    >[!NOTE]
    >Há um atraso de até 48 horas entre a hora em que uma subscrição muda e quando o evento Atualizado de Subscrição é ativado.

- **Evento Excededo limiar ("usagerecords-thresholdExceeded")**

    Este evento é angariado quando o montante de Microsoft Azure utilização para qualquer cliente excede o seu orçamento de gastos de utilização (o seu limiar). Para obter mais informações, consulte [Desconfiem de um orçamento de gastos Azure para os seus clientes/parceiro-centro/set-an-azure-spend-budget-for-your-customers).

- **Evento Criado de Referência ("Referenciação-criado")**

    Este evento é levantado quando a referência é criada.

- **Evento Atualizado de Referência ("referenciação atualizada")**

    Este evento é levantado quando a referência é atualizada.

- **Evento pronto para faturas ("pronto para fatura")**

    Este evento é levantado quando a nova fatura estiver pronta.

Os eventos do Future Webhook serão adicionados para recursos que mudam no sistema que o parceiro não controla, e serão feitas novas atualizações para obter esses eventos o mais perto possível do "tempo real". O feedback dos Parceiros sobre quais os eventos que acrescentam valor ao seu negócio será útil para determinar que novos eventos adicionar.

Para obter uma lista completa de eventos Webhook apoiados pelo Partner Center, consulte [os eventos webhook do Partner Center](partner-center-webhook-events.md).

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação do Partner Center](partner-center-authentication.md). Este cenário suporta a autenticação com as credenciais de App autónoma e App+User.

## <a name="receiving-events-from-partner-center"></a>Receber eventos do Partner Center

Para receber eventos do Partner Center, deve expor um ponto final acessível ao público. Como este ponto final está exposto, deve validar que a comunicação é do Centro de Parceiros. Todos os eventos Webhook que recebe são assinados digitalmente com um certificado que acorra ao Microsoft Root. Será também fornecido um link para o certificado utilizado para assinar o evento. Isto permitirá que o certificado seja renovado sem que tenha de reimplantar ou reconfigurar o seu serviço. O Partner Center fará 10 tentativas para entregar o evento. Se o evento ainda não for entregue após 10 tentativas, será movido para uma fila offline e não serão feitas mais tentativas na entrega.

A amostra que se segue mostra um evento publicado no Partner Center.

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
>O cabeçalho de autorização tem um esquema de "Assinatura". Esta é uma assinatura codificada base64 do conteúdo.

## <a name="how-to-authenticate-the-callback"></a>Como autenticar o retorno

Para autenticar o evento de retorno recebido do Partner Center, siga estes passos:

1. Verifique se os cabeçalhos necessários estão presentes (Autorização, x-ms-certificate-url, x-ms-signature-algorithm).

2. Faça o download do certificado utilizado para assinar o conteúdo (x-ms-certificate-url).

3. Verifique a cadeia de certificados.

4. Verifique a "Organização" do certificado.

5. Leia o conteúdo com a codificação utf8 num tampão.

6. Crie um RSA Crypto Provider.

7. Verifique os dados correspondem ao que foi assinado com o algoritmo de haxixe especificado (por exemplo, SHA256).

8. Se a verificação for bem sucedida, processe a mensagem.

> [!NOTE]
> Por predefinição, o token de assinatura será enviado num cabeçalho de autorização. Se definir **SignatureTokenToMsSssignatureHeader** para ser verdadeiro no seu registo, o token de assinatura será enviado no cabeçalho de assinatura x-ms.

## <a name="event-model"></a>Modelo de evento

A tabela seguinte descreve as propriedades de um evento partner center.

### <a name="properties"></a>Propriedades

| Nome                      | Descrição                                                                           |
|---------------------------|---------------------------------------------------------------------------------------|
| **EventName**             | O nome do evento. No formulário {recurso}-{ação}. Por exemplo, "testado".  |
| **RecursosUri**           | O URI do recurso que mudou.                                                 |
| **Nome de recursos**          | O nome do recurso que mudou.                                                |
| **AuditUrl**              | Opcional. O URI do registo de auditoria.                                                |
| **ResourceChangeUtcDate** | A data e a hora, no formato UTC, quando ocorreu a alteração de recursos.                  |

### <a name="sample"></a>Sample

A amostra que se segue mostra a estrutura de um evento do Partner Center.

```http
{
    "EventName": "test-created",
    "ResourceUri": "http://api.partnercenter.microsoft.com/webhooks/v1/registration/validationEvents/c0bfd694-3075-4ec5-9a3c-733d3a890a1f",
    "ResourceName": "test",
    "AuditUri": null,
    "ResourceChangeUtcDate": "2017-11-16T16:19:06.3520276+00:00"
}
```

## <a name="webhook-apis"></a>Webhook APIs

### <a name="authentication"></a>Autenticação

Todas as chamadas para as APIs webhook são autenticadas usando o token do portador no cabeçalho de autorização. Adquira um token de acesso ao `https://api.partnercenter.microsoft.com` acesso. Este token é o mesmo símbolo que é usado para aceder ao resto das APIs do Centro De Parceiros.

### <a name="get-a-list-of-events"></a>Obtenha uma lista de eventos

Devolve uma lista dos eventos que são atualmente suportados pelas APIs do Webhook.

### <a name="resource-url"></a>URL do recurso

`https://api.partnercenter.microsoft.com/webhooks/v1/registration/events`

### <a name="request-example"></a>Exemplo de pedido

```http
GET /webhooks/v1/registration/events
content-type: application/json
authorization: Bearer eyJ0e.......
accept: */*
host: api.partnercenter.microsoft.com
```

### <a name="response-example"></a>Exemplo de resposta

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

### <a name="register-to-receive-events"></a>Registe-se para receber eventos

Regista um inquilino para receber os eventos especificados.

#### <a name="resource-url"></a>URL do recurso

`https://api.partnercenter.microsoft.com/webhooks/v1/registration`

### <a name="request-example"></a>Exemplo de pedido

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

### <a name="response-example"></a>Exemplo de resposta

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

### <a name="view-a-registration"></a>Ver um registo

Devolve o registo do evento Webhooks a um inquilino.

#### <a name="resource-url"></a>URL do recurso

`https://api.partnercenter.microsoft.com/webhooks/v1/registration`

### <a name="request-example"></a>Exemplo de pedido

```http
GET /webhooks/v1/registration
Content-Type: application/json
Authorization: Bearer ...
Accept: */*
Host: api.partnercenter.microsoft.com
Accept-Encoding: gzip, deflate
```

### <a name="response-example"></a>Exemplo de resposta

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

### <a name="update-an-event-registration"></a>Atualizar um registo de eventos

Atualiza um registo de eventos existente.

#### <a name="resource-url"></a>URL do recurso

`https://api.partnercenter.microsoft.com/webhooks/v1/registration`

### <a name="request-example"></a>Exemplo de pedido

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

### <a name="response-example"></a>Exemplo de resposta

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

### <a name="send-a-test-event-to-validate-your-registration"></a>Envie um evento de teste para validar o seu registo

Gera um evento de teste para validar o registo webhooks. Este teste destina-se a validar que pode receber eventos do Partner Center. Os dados para estes eventos serão eliminados sete dias após a criação do evento inicial. Tem de estar registado para o evento "test-created", utilizando a API de registo, antes de enviar um evento de validação.

>[!NOTE]
>Existe um limite de aceleração de 2 pedidos por minuto ao publicar um evento de validação.

#### <a name="resource-url"></a>URL do recurso

`https://api.partnercenter.microsoft.com/webhooks/v1/registration/validationEvents`

### <a name="request-example"></a>Exemplo de pedido

```http
POST /webhooks/v1/registration/validationEvents
MS-CorrelationId: 3ef0202b-9d00-4f75-9cff-15420f7612b3
Authorization: Bearer ...
Accept: */*
Host: api.partnercenter.microsoft.com
Accept-Encoding: gzip, deflate
Content-Length:
```

### <a name="response-example"></a>Exemplo de resposta

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

### <a name="verify-that-the-event-was-delivered"></a>Verifique se o evento foi entregue

Devolve o estado atual do evento de validação. Esta verificação pode ser útil para resolver problemas de entrega de eventos. A Resposta contém um resultado para cada tentativa que é feita para entregar o evento.

#### <a name="resource-url"></a>URL do recurso

`https://api.partnercenter.microsoft.com/webhooks/v1/registration/validationEvents/{correlationId}`

### <a name="request-example"></a>Exemplo de pedido

```http
GET /webhooks/v1/registration/validationEvents/04af2aea-d413-42db-824e-f328001484d1
MS-CorrelationId: 3ef0202b-9d00-4f75-9cff-15420f7612b3
Authorization: Bearer ...
Accept: */*
Host: api.partnercenter.microsoft.com
Accept-Encoding: gzip, deflate
```

### <a name="response-example"></a>Exemplo de resposta

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

## <a name="example-for-signature-validation"></a>Exemplo para Validação de Assinaturas

### <a name="sample-callback-controller-signature-aspnet"></a>Assinatura do controlador de chamada de amostra (ASP.NET)

``` csharp
[AuthorizeSignature]
[Route("webhooks/callback")]
public IHttpActionResult Post(PartnerResourceChangeCallBack callback)
```

### <a name="signature-validation"></a>Validação de assinaturas

O exemplo a seguir mostra como adicionar um Atributo de Autorização ao controlador que está a receber chamadas de eventos webhook.

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
