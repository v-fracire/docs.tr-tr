---
title: .NET mikro Hizmetleri. Kapsayıcılı .NET uygulamaları mimarisi
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Mikro hizmetler, modüler ve bağımsız bir şekilde dağıtılabilen hizmetleridir. Docker kapsayıcıları (için Linux ve Windows), dağıtım ve bir hizmeti ve bağımlılıklarını ardından yalıtılmış bir ortamda çalıştırılır tek bir birim halinde paketleme tarafından test basitleştirin.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 08/31/2018
ms.openlocfilehash: 0f401f89b0a568b8dc7c3734b2f06fa3a14de110
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47088503"
---
# <a name="net-microservices-architecture-for-containerized-net-applications"></a>.NET mikro Hizmetleri: Kapsayıcılı .NET uygulamaları mimarisi

![Kitap kapsar](./media/cover-small.png)

**Sürüm v2.1.02** - ASP.NET Core 2.1 için güncelleştirilmiş

Mikro hizmet tabanlı uygulamaları geliştirmek ve bunları yönetmek için giriş niteliğindeki bu kılavuzda, kapsayıcıları kullanma. Mimari Tasarım açıklar ve .NET Core ve Docker kapsayıcılarını kullanarak uygulama yaklaşıyor. 

Başlama daha kolay hale getirmek için bir kapsayıcıya alınmış başvuru ve keşfedebilirsiniz mikro hizmet tabanlı uygulama Kılavuzu odaklanır. Başvuru uygulama kullanılabilir [hizmetine](https://github.com/dotnet-architecture/eShopOnContainers) GitHub deposu.

## <a name="action-links"></a>Eylem bağlantıları

* Tercih ettiğiniz biçimdeki bu e-kitabı indirin: | [PDF](https://aka.ms/microservicesebook) | [MOBI](https://www.microsoft.com/net/download/thank-you/microservices-architecture-ebook-mobi) | [EPUB](https://www.microsoft.com/net/download/thank-you/microservices-architecture-ebook-epub) |

* Kopyalama/çatal başvurusu [hizmetine github'da](https://github.com/dotnet-architecture/eShopOnContainers)
 
* İzleme [tanıtım videosunu Channel 9](http://aka.ms/microservices-video)

* Tanıyalım [mikro hizmet mimarisi](http://aka.ms/MicroservicesArchitecture) hemen

## <a name="introduction"></a>Giriş

Kuruluşların giderek daha fazla maliyet tasarrufu taahhüdünü gerçekleştirmeye dağıtım sorunlarını giderme ve kapsayıcıları kullanarak DevOps ve üretim işlemleri iyileştirme. Microsoft Windows ve Linux kapsayıcı yenilikten Azure Container Service ve Azure Service Fabric gibi ürünleri oluşturarak ve Docker, Mesosphere ve Kubernetes gibi sektör öncüleri ile işbirliği yapan mıt'li serbest. Bu ürünler, bulut hızı ve ölçeği, hangi uygulamaları derlemeye ve dağıtmaya şirketlerin yardımcı kapsayıcı çözümler sunmak kendi seçtiğiniz platform veya araçları.

Docker kapsayıcı sektördeki en önemli Windows ve Linux eko satıcılar tarafından desteklenen, pratikte bir standart hale gelmektedir. (Microsoft, Docker'ı destekleyen temel bulut satıcıları biridir.) Gelecekte, Docker büyük olasılıkla bulutta veya şirket içinde herhangi bir veri merkezinde bulunabilen olacaktır.

Ayrıca, [mikro Hizmetler](https://martinfowler.com/articles/microservices.html) mimarisi Gelişmekte olan dağıtılmış görev açısından kritik uygulamalar için önemli bir yaklaşım. Mikro hizmet tabanlı bir mimaride, uygulama koleksiyonu, test edilmiş, dağıtılan ve tutulan bağımsız olarak geliştirilebilir hizmetleri üzerinde oluşturulmuştur.

## <a name="about-this-guide"></a>Bu kılavuz hakkında

Mikro hizmet tabanlı uygulamaları geliştirmek ve bunları yönetmek için giriş niteliğindeki bu kılavuzda, kapsayıcıları kullanma. Mimari Tasarım açıklar ve .NET Core ve Docker kapsayıcılarını kullanarak uygulama yaklaşıyor. Kapsayıcılar ve mikro hizmetler kullanmaya başlama daha kolay hale getirmek için bir kapsayıcıya alınmış başvuru ve keşfedebilirsiniz mikro hizmet tabanlı uygulama Kılavuzu odaklanır. Örnek uygulamayı kullanılabilir [hizmetine](https://github.com/dotnet-architecture/eShopOnContainers) GitHub deposu.

Bu kılavuz iki teknoloji odaklanan temel geliştirme ve öncelikli olarak geliştirme ortamı düzeyde mimari rehberlik sağlar: Docker ve .NET Core. Bizim engellemekse altyapıya üretim ortamınızın (Bulut veya şirket içi) odaklanmadan uygulama tasarımınızı düşünürken, bu kılavuzu okumadan ' dir. Üretime hazır uygulamalar oluşturduğunuzda, altyapı konusunda kararlar daha sonra yapar. Bu nedenle, bu kılavuz dilden bağımsız ve daha fazla geliştirme ortamı-merkezli altyapı olması amaçlanmıştır.

Bu kılavuzda eğitim sonra Microsoft Azure üzerinde üretime hazır mikro hizmetler hakkında bilgi edinmek için sonraki adımınız olacaktır.

## <a name="version"></a>Sürüm

Bu kılavuzda kaplayacak şekilde yeniden düzenlendi **.NET Core 2.1** yanı sıra birçok ek güncelleştirme sürümü ilgili aynı "(yani. wave" teknolojileri Azure ve ek 3. taraf teknolojileri) ile .NET Core 2.1 zamanlı durdurulmasıyla. İşte bu kitap sürümü de sürümüne güncelleştirildi **2.1**. 

## <a name="what-this-guide-does-not-cover"></a>Ne bu kılavuzda ele alınmamaktadır

Bu kılavuz, uygulama yaşam döngüsü üzerinde DevOps, CI/CD işlem hatları, odaklı değildir veya takım iş. Tamamlayıcı Kılavuzu [kapsayıcılı Docker uygulaması yaşam döngüsü Microsoft Platformu ve araçları ile](https://aka.ms/dockerlifecycleebook) Bu konu üzerinde odaklanır. Geçerli Kılavuz ayrıca uygulama ayrıntıları gibi belirli düzenleyicileri bilgi Azure altyapı sağlamaz.

### <a name="additional-resources"></a>Ek kaynaklar

-   **Docker uygulaması yaşam döngüsü Microsoft Platformu ve araçları ile kapsayıcılı hale** (indirilebilir e-kitap)  
    [*https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)

## <a name="who-should-use-this-guide"></a>Bu kılavuzda kullanan

Geliştiriciler ve Docker tabanlı uygulama geliştirmeyi ve mikro hizmet tabanlı mimari için yeni olan çözüm mimarları için bu kılavuzu yazdığımız. Mimari hakkında bilgi edinmek isterseniz tasarlamanıza ve kavram kanıtı uygulamalarını (.NET Core odaklanmaktadır ile) Microsoft geliştirme teknolojileri ile uygulamak için bu kılavuzda sunulmaktadır ve Docker kapsayıcıları ile.

Ayrıca bu kılavuzun yararlı bir mimari isteyen bir kuruluş Mimarı'gibi bir teknik karar mercii olan ve teknoloji genel bakış, önce karar verirseniz dağıtılmış uygulamalar yeni ve modern seçmek için hangi yaklaşımı hakkında bulabilirsiniz.

### <a name="how-to-use-this-guide"></a>Bu kılavuz nasıl kullanılır?

Bu kılavuzun ilk bölümü Docker kapsayıcıları sunar, .NET Core ve geliştirme framework .NET Framework arasında seçim anlatılmaktadır ve mikro hizmetler için genel bir bakış sağlar. Bu içerik mimarları ve genel bir bakış istiyor ancak kod uygulaması ayrıntılara odaklanmak gerekmez teknik karar verenler içindir.

İle başlayan Kılavuzu ikinci bölümü [geliştirme süreci için Docker tabanlı uygulamalar](./docker-application-development-process/index.md) bölümü. .NET Core ve Docker kullanan uygulamalar, uygulama geliştirme ve mikro hizmet desenleri odaklanır. Bu bölümde, geliştiricilere ve mimarlara desenleri ve uygulama ayrıntılarını ve kod üzerinde odaklanmak isteyen çoğu ilgi olacaktır.

## <a name="related-microservice-and-container-based-reference-application-eshoponcontainers"></a>Mikro hizmet ve kapsayıcı tabanlı başvuru uygulaması ilgili: hizmetine

.NET Core ve Docker kapsayıcılarını kullanarak dağıtılması için tasarlanmış bir mikro hizmetler için açık kaynak başvuru uygulama hizmetine uygulamasıdır. Uygulama birden çok e-store UI ön uçlar (bir MVC Web uygulaması, Web SPA ve yerel bir mobil uygulama) dahil olmak üzere birden çok alt oluşur. Ayrıca arka uç mikro hizmetler ve kapsayıcılar için gerekli tüm sunucu tarafı işlemleri içerir. 

Mimari desenleri göstermek için uygulama amacı olan. **BT değil bir ÜRETİME hazır şablonu** gerçek uygulamaları başlatmak için. Ayrıca bunlar gösterildiği gibi yeni ilginç olabilecek teknolojileri test etmek için kullanılır, uygulama bir kalıcı beta durumda aynıdır.

## <a name="send-us-your-feedback"></a>Bize geri bildirim gönderin!

Kapsayıcılı uygulamaları ve .NET içinde mikro hizmetler mimarisi anlamanıza yardımcı olması için bu kılavuzu yazdığımız. Bildirimleriniz bizim için değerli şekilde Kılavuzu ve ilgili başvuru uygulaması, gelişen! Bu kılavuz nasıl geliştirilebilir hakkında açıklamalar varsa, Lütfen bunları gönderin:

[dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com)

## <a name="credits"></a>Krediler

Ortak yazarlar:

> **Cesar de la Torre**, üst düzey PM, .NET ürün ekibi, Microsoft Corp.
>
> **Fatura Wagner**, üst düzey İçerik geliştirici, C + E, Microsoft Corp.
>
> **Mike Rousos**, baş yazılım mühendisi, Devdiv'e CAT ekibi, Microsoft

Düzenleyiciler:

> **Mike Pope**
>
> **Steve Hoag**

Katılımcılar ve gözden geçirenler:

> **Jeffrey Richter**, iş ortağı yazılım Mühendisliği, Azure ekibi, Microsoft
>
> **Jimmy Bogard**, Headspring, baş Mimar
>
> **UDI Dahan**, kurucu ve CEO, belirli yazılım
>
> **Jimmy Nilsson**, ortak kurucu ve CEO, Factor10
>
> **Glenn Condron**, üst düzey Program Yöneticisi, ASP.NET takımı
>
> **İşareti Fussell**, asıl PM lideri, Microsoft Azure Service Fabric ekibi
>
> **Diego Vega**, PM lideri, Entity Framework takım, Microsoft
>
> **Barry Dorrans**, üst düzey Güvenlik Program Yöneticisi
>
> **Rowan Miller**, üst düzey Program Yöneticisi, Microsoft
>
> **Ankit Asthana**, baş PM Yöneticisi, Microsoft .NET ekibi
>
> **Scott Hunter**, .NET ekibi, Microsoft iş ortağı Direktörü PM
>
> **Dylan Reisenberger**, Mimar ve Polly Bykov'un geliştirme
>
> **Steve Smith**, yazılım mesleğini geliştirme & ASPSmith Ltd., eğitmen
>
> **Ian Cooper**, kodlama mimari en parlak
>
> **Unai Zorrilla**, mimari ve geliştirme Bykov'un düz kavramları
>
> **Eduard Tomas**, geliştirme Bykov'un düz kavramları
>
> **Ramon Tomas**, düz kavramları geliştiricisi
>
> **David Sanz**, düz kavramları geliştiricisi
>
> **Javier Valero**, Enformasyon Müdürü Grupo çözümleri işletim
>
> **Pierre Millet**, üst düzey Danışman, Microsoft
>
> **Michael Friis**, ürün Yöneticisi, Docker Inc.
>
> **Charles Lowell**, yazılım mühendisi, VS CAT ekibi, Microsoft
>
> **Miguel Veloso**, üst düzey Danışman Turing sınaması sırasında


## <a name="copyright"></a>Telif Hakkı

İNDİRME bulunabilir: <https://aka.ms/microservicesebook>

TARAFINDAN YAYIMLANAN

Microsoft Geliştirici bölme, .NET ve Visual Studio ürün takımları

Microsoft Corporation'ın bir bölme

One Microsoft Way

Redmond, Washington 98052-6399

Telif Hakkı © 2018 Microsoft Corporation

Tüm hakları saklıdır. Bu kitap içeriğini bir parçası çoğaltılamaz veya herhangi bir araçla yayımcı yazılı izni olmadan herhangi bir biçimdeki aktarılamaz.

Bu kitap sağlanan "olarak-olduğunu" ve yazarın görünümleri ve düşünceleri son derece ifade eder. Görünümleri ve düşünceleri son derece bilgi URL ve diğer Internet Web sitesi referansları da dahil olmak üzere bu kitap, ifade verilmeksizin değiştirilebilir.

Burada açıklanan bazı örnekler yalnızca çizim için sağlanmıştır ve bu kurgusaldır. Gerçek bir ilişki veya bağlantı amaçlanmamıştır veya çıkarılmamalıdır.

Microsoft ve adresinde listelenmiş ticari http://www.microsoft.com "Ticari" Web sayfasında Microsoft şirketler grubunun ticari markalarıdır.

Mac ve macOS Apple Inc.'in ticari markalarıdır.

Docker whale logosu, Docker, Inc.'in kayıtlı ticari markasıdır. İzni tarafından kullanılır.

Diğer tüm işaretleri ve logoları sahiplerinin özelliği var.


>[!div class="step-by-step"]
[Next](container-docker-introduction/index.md)
