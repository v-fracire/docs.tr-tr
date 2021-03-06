---
title: İle Polly üstel geri alma ile HTTP çağrı yeniden uygulayın
description: Polly ile HttpClientFactory HTTP hatalarını işlemek hakkında bilgi edinin
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/10/2018
ms.openlocfilehash: c16f4c0f2ef09f346c8b46ff8089883cedcf0c7e
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37874903"
---
# <a name="implement-http-call-retries-with-exponential-backoff-with-httpclientfactory-and-polly-policies"></a>HttpClientFactory ve Polly üstel geri alma ile HTTP çağrı yeniden uygulayın

Açık kaynak gibi daha gelişmiş .NET kitaplıkları yararlanmak için üstel geri alma ile yeniden denemeler için önerilen bir yaklaşım olan [Polly kitaplığını](https://github.com/App-vNext/Polly).

Polly esnekliği ve geçici hata işleme özellikleri sağlayan bir .NET Kitaplığı ' dir. Bu özellikler, yeniden deneme, devre kesici, bölme perdesi yalıtım, zaman aşımı ve geri dönüş gibi Polly ilkeleri uygulayarak uygulayabilirsiniz. Polly hedefleyen .NET 4.x ve .NET Standard kitaplığı (.NET Core destekleyen) 1.0.

Ancak, kendi özel kodunuzu içeren HttpClient Polly'nın kitaplığı kullanarak önemli ölçüde karmaşık olabilir. Hizmetine özgün sürümünde oluştu bir [ResilientHttpClient Yapı Taşı](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/Resilience/Resilience.Http/ResilientHttpClient.cs) Polly üzerinde temel. Ancak, böylece yapı taşı hizmetine kullanım dışı bırakıldı HttpClientFactory'nın yayınlanmasıyla birlikte, Http iletişimi için dayanıklı uygulamak, çok daha kolay olur. 

Aşağıdaki adımlar, Http nasıl kullanabileceğinizi gösterir önceki bölümde açıklanan HttpClientFactory, yeniden denemeler Polly ile tümleştirilir.

**ASP.NET Core 2.1 referans paketleri**

NuGet kullanarak ASP.NET Core 2.1 paketleri bitvise projeniz vardır. Genelde gerekir `AspNetCore` metapackage ve uzantı paketi `Microsoft.Extensions.Http.Polly`.

**Polly'nın yeniden deneme ilkesi, başlatma ile istemci yapılandırma**

Önceki bölümlerde gösterildiği gibi adlandırılmış veya türü belirtilmiş bir istemci HttpClient yapılandırma, standart Startup.ConfigureServices(...) yöntemi tanımlamak gerekir, ancak şimdi, üstel geri alma ile Http yeniden deneme ilkesi olarak belirterek artımlı kod ekleyin Aşağıda:

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to five minutes
        .AddPolicyHandler(GetRetryPolicy());
```

**AddPolicyHandler()** yöntemdir hangi ilkeleri ekler `HttpClient` nesnelerini kullanırsınız. Bu durumda, bunu Polly'nın ilke Http yeniden deneme için üstel geri alma ile eklemektir.

Daha modüler bir yaklaşım sahip olmak için Http yeniden deneme ilkesi ConfigureServices() yöntemi içinde ayrı bir yöntem aşağıdaki kodu tanımlanabilir.

```csharp
static IAsyncPolicy<HttpResponseMessage> GetRetryPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .OrResult(msg => msg.StatusCode == System.Net.HttpStatusCode.NotFound)
        .WaitAndRetryAsync(6, retryAttempt => TimeSpan.FromSeconds(Math.Pow(2,
                                                                    retryAttempt)));
}
```

Polly ile yeniden denemeler, üstel geri alma yapılandırmasını ve hata günlük kaydı gibi bir HTTP özel durum olduğunda gerçekleştirilecek eylemleri sayısı bir yeniden deneme ilkesi tanımlayabilirsiniz. Bu durumda, ilke ile iki saniyede bir üstel yeniden deneme altı kat denemek için yapılandırılır. 

Bu nedenle altı kat deneyecek ve her yeniden deneme arasındaki saniye iki saniye cinsinden başlangıç üstel, olacaktır.

### <a name="adding-a-jitter-strategy-to-the-retry-policy"></a>Değişimi stratejisi için yeniden deneme ilkesi ekleme

Normal bir yeniden deneme ilkesi, sisteminizin durumlarda yüksek eşzamanlılık ve ölçeklenebilirlik ve yüksek Çekişme altında etkileyebilir. En yüksek sayılar kısmi kesintiler durumunda birçok istemcilerden gelen benzer bir yeniden deneme aşmak için iyi bir geçici çözüm değişimi stratejisi için yeniden deneme algoritması/İlkesi eklemektir. Rastgele üstel geri alma için ekleyerek bu uçtan uca sistemin genel performansı artırabilir. Sorunlar ortaya çıktığında bunu ani değişiklikleri yayar. Değişimi uygulamak için kodu, düz bir Polly İlkesi kullandığınızda, aşağıdaki örnekteki gibi görünebilir:

```csharp
Random jitterer = new Random(); 
Policy
  .Handle<HttpResponseException>() // etc
  .WaitAndRetry(5,    // exponential back-off plus some jitter
      retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt))  
                    + TimeSpan.FromMilliseconds(jitterer.Next(0, 100)) 
  );
```

## <a name="additional-resources"></a>Ek kaynaklar

-   **Yeniden deneme düzeni**
    [*https://docs.microsoft.com/azure/architecture/patterns/retry*](https://docs.microsoft.com/azure/architecture/patterns/retry)

-   **Polly ve HttpClientFactory**
    [*https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory*](https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory)

-   **Polly (.NET esnekliği ve geçici hata işleme kitaplığı)**

    [*https://github.com/App-vNext/Polly*](https://github.com/App-vNext/Polly)

-   **Marc Brooker. Değişimi: Şeyler doğrulukla ile daha iyi hale**

    [*https://brooker.co.za/blog/2015/03/21/backoff.html*](https://brooker.co.za/blog/2015/03/21/backoff.html)



>[!div class="step-by-step"]
[Önceki](explore-custom-http-call-retries-exponential-backoff.md)
[İleri](implement-circuit-breaker-pattern.md)
