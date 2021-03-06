---
title: .NET core dağıtım paketleme
description: Paket, öğrenin adını ve dağıtım için .NET Core sürümü.
author: bleroy
ms.author: mairaw
ms.date: 06/28/2017
ms.openlocfilehash: 084de6bbb3ce280beb0846431aeceacbb57d9a32
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33217408"
---
# <a name="net-core-distribution-packaging"></a>.NET core dağıtım paketleme

.NET Core daha da fazla platformlarda kullanılabilir hale geldiğinde, adı, paket hakkında bilgi edinmek yararlı olacaktır ve sürümü. Bu şekilde, paket maintainers burada .NET çalıştırmak kullanıcıları seçin olsun tutarlı bir deneyim sağlamaya yardımcı olabilir.

## <a name="disk-layout"></a>Disk düzeni

Yüklendiğinde, .NET Core gibi dosya sistemi layed çıkışı birçok bileşenden oluşur:

```
.
├── dotnet                       (1)
├── LICENSE.txt                  (8)
├── ThirdPartyNotices.txt        (8)
├── host
│   └── fxr
│       └── <fxr version>        (2)
├── sdk
│   ├── <sdk version>            (3)
│   └── NuGetFallbackFolder      (4)
└── shared
    ├── Microsoft.NETCore.App
    │   └── <runtime version>    (5)
    └── Microsoft.AspNetCore.App
        └── <aspnetcore version> (6)
    └── Microsoft.AspNetCore.All
        └── <aspnetcore version> (7)
/
├─usr/share/man/man1
│       └── dotnet.1.gz          (9)
└─usr/bin
        └── dotnet               (10)
```

- (1) **dotnet** ana bilgisayar (olarak da bilinen "Karıştırıcı") iki ayrı rolleri içerir: uygulamayı başlatmak için bir çalışma zamanı etkinleştirmek ve komutları ona çözümlenebilen bir SDK etkinleştirin. Ana bilgisayarın yerel bir yürütülebilir dosya olduğunu (`dotnet.exe`).

Tek bir ana bilgisayar olsa da, diğer bileşenleri sürümlü dizinleri (2,3,5,6) durumdadır. Yüklü yan yana olduğundan bu yollar birden çok sürümü sistemde mevcut olabilir.

- (2) **konak/fxr/\<fxr sürüm >** ana bilgisayar tarafından kullanılan çerçeve çözümlemesi mantığını içerir. Ana bilgisayar yüklü en son hostfxr kullanır. .NET Core uygulama yürütülürken uygun çalışma zamanı seçmek için hostfxr sorumludur. Örneğin, .NET Core 2.0.0 2.0.5 kullanacağı için oluşturulmuş bir uygulama kullanılabilir olduğunda çalışma zamanı. Benzer şekilde, hostfxr uygun SDK geliştirme sırasında seçer.

- (3) **sdk /\<sdk sürümü >** (olarak da bilinen "Araçları") SDK yazma ve .NET Core kitaplıkları ve uygulamaları oluşturmak için kullanılan yönetilen araçları kümesidir. SDK, CLI, Roslyn derleyici, MSBuild, ilişkili derleme görev ve hedeflerini, NuGet, yeni proje şablonları, vb. içerir.

- (4) **sdk/NuGetFallbackFolder** sırasında bir SDK'sı tarafından kullanılan NuGet paketleri önbelleği içeren `dotnet restore` adım.

**Paylaşılan** çerçeveleri içeren klasör. Farklı uygulama tarafından kullanılabilmesi için merkezi bir konumda bir dizi paylaşılan bir çerçeve sağlar.

- (5) **shared/Microsoft.NETCore.App/\<çalışma zamanı sürümü >** bu framework .NET çekirdeği çalışma zamanı ve destekleyici yönetilen kitaplıklarını içerir.

- (6,7) **shared/Microsoft.AspNetCore. { Uygulama, tüm} /\<aspnetcore sürüm >** ASP.NET Core kitaplıkları içerir. Kitaplıkları altında `Microsoft.AspNetCore.App` geliştirilen ve .NET Core projenin bir parçası olarak desteklenir. Kitaplıkları altında `Microsoft.AspNetCore.All` 3 taraf kitaplıkları da içeren bir alt kümesi olan.

- (8) **LICENSE.txt,ThirdPartyNotices.txt** .NET Core lisans ve lisansları .NET Core kullanılan üçüncü taraf kitaplıkların.

- (9,10) **dotnet.1.gz, dotnet** `dotnet.1.gz` dotnet adam sayfasıdır. `dotnet` Simgesel dotnet host(1) için olur. Bu dosyalar, sistem tümleştirmesi için iyi bilinen konumlara yüklenir.

## <a name="recommended-packages"></a>Önerilen paketleri

.NET core sürüm oluşturma çalışma zamanı bileşeni temel `[major].[minor]` sürüm numaraları.
SDK sürümü aynı kullanan `[major].[minor]` ve bağımsız `[patch]` için SDK'sı özelliği ve düzeltme eki semantiği birleştirir.
Örneğin: SDK sürüm 2.2.302 bir 2.2 çalışma zamanı destekler SDK'ın 3 özelliği sürüm 2 düzeltme eki sürümü.

Bazı paketler adında sürüm numarasını parçası içerir. Bu, belirli bir sürümünü yüklemek son kullanıcı sağlar.
Sürümü geri kalanı sürüm adı dahil edilmez. Bu işletim sistemi Paket Yöneticisi'nin güncelleştirme (örn. güvenlik otomatik olarak yükleme giderir) paketleri sağlar.

Aşağıdaki tablolarda önerilen paketleri gösterir.

| Ad                                    | Örnek                | Kullanım örneği: yükle...           | İçerir           | Bağımlılıklar                                   | Sürüm            |
|-----------------------------------------|------------------------|---------------------------------|--------------------|------------------------------------------------|--------------------|
| dotnet-sdk-[major]                      | dotnet-sdk-2           | Çalışma zamanı ana için en son SDK'sı    |                    | DotNet - sdk-[Temel]. [latestminor]               | \<SDK sürümü >     |
| DotNet - sdk-[Temel]. [alt]              | DotNet sdk 2.1         | Belirli bir çalışma zamanı için en son SDK'sı |                    | DotNet - sdk-[Temel]. [alt]. [son sdk feat] xx | \<SDK sürümü >     |
| DotNet - sdk-[Temel]. [alt]. [sdk feat] xx | DotNet sdk 2.1.3xx     | Belirli sdk özellik sürüm    | (3),(4)            | aspnetcore - çalışma zamanı-[Temel]. [alt]             | \<SDK sürümü >     |
| aspnetcore - çalışma zamanı-[Temel]. [alt]      | aspnetcore çalışma zamanı 2.1 | Belirli ASP.NET çekirdeği çalışma zamanı   | (6),[(7)]          | DotNet - çalışma zamanı-[Temel]. [alt]                 | \<çalışma zamanı sürümü > |
| DotNet - çalışma zamanı-[Temel]. [alt]          | DotNet çalışma zamanı 2.1     | Belirli bir çalışma zamanı                | (5)                | ana bilgisayar fxr:\<çalışma zamanı sürümü > +                   | \<çalışma zamanı sürümü > |
| dotnet-host-fxr                         | dotnet-host-fxr        | _bağımlılık_                    | (2)                | ana bilgisayar:\<çalışma zamanı sürümü > +                       | \<çalışma zamanı sürümü > |
| DotNet ana bilgisayar                             | DotNet ana bilgisayar            | _bağımlılık_                    | (1),(8),(9),(10)   |                                                | \<çalışma zamanı sürümü > |

Çoğu dağıtımları kaynağından oluşturulacak tüm yapıları gerektirir. Bu paketleri bazı etkisi vardır:

- 3 taraf kitaplıkları altında `shared/Microsoft.AspNetCore.All` kaynağından kolayca oluşturulamıyor. Bu klasör gelen atlanmış biçimde `aspnetcore-runtime` paket.

- `NuGetFallbackFolder` İkili yapılardan kullanılarak doldurulur `nuget.org`. Boş kalmalıdır.

Birden çok `dotnet-sdk` paketler için aynı dosyaları sağlayabilir `NuGetFallbackFolder`. Paket Yöneticisi ile sorunlarını önlemek için bu dosyaları aynı olmalıdır (sağlama toplamı, değiştirilme tarihi,...).

#### <a name="preview-versions"></a>Önizleme sürümleri

Paket maintainers Önizleme paylaşılan framework sürümleri ve SDK sağlamak karar verebilirsiniz. Önizleme sürümleri kullanılarak sağlanmalıdır `dotnet-sdk-[major].[minor].[sdk feat]xx`, `aspnetcore-runtime-[major].[minor]`, `dotnet-runtime-[major].[minor]` paketler. Önizleme sürümleri için önemli Paket sürümü sıfır olarak ayarlanması gerekir. Bu şekilde son sürüm yükseltme paketi olarak yüklenir.

#### <a name="patch-packages"></a>Düzeltme eki paketleri

Bir paket düzeltme eki sürümü önemli bir değişiklik neden olabilir olduğundan, bir paket Bakımcı sağlamak isteyebilirsiniz _düzeltme eki paketleri_. Bu paketleri sağlar, otomatik olarak yükseltilmez belirli düzeltme eki sürümü yüklemek için. (Güvenlik) ile yükseltilmiş düzeltmeleri olmayacak şekilde eki paketlerini yalnızca ender durumlarda kullanılmalıdır.

Aşağıdaki tabloda önerilen paketleri gösterir ve **düzeltme eki paketleri**.

| Ad                                           | Örnek                  | İçerir         | Bağımlılıklar                                              |
|------------------------------------------------|--------------------------|------------------|-----------------------------------------------------------|
| dotnet-sdk-[major]                             | dotnet-sdk-2             |                  | DotNet - sdk-[Temel]. [ikincil son sdk]                     |
| DotNet - sdk-[Temel]. [alt]                     | DotNet sdk 2.1           |                  | DotNet - sdk-[Temel]. [alt]. [son sdk feat] xx            |
| DotNet - sdk-[Temel]. [alt]. [sdk feat] xx        | DotNet sdk 2.1.3xx       |                  | DotNet - sdk-[Temel]. [alt]. [son sdk düzeltme]             |
| **DotNet - sdk-[Temel]. [alt]. [düzeltme]**         | DotNet sdk 2.1.300       | (3),(4)          | aspnetcore - çalışma zamanı-[Temel]. [alt]. [sdk çalışma zamanı düzeltme]    |
| aspnetcore - çalışma zamanı-[Temel]. [alt]             | aspnetcore çalışma zamanı 2.1   |                  | aspnetcore - çalışma zamanı-[Temel]. [alt]. [son çalışma zamanı düzeltme] |
| **aspnetcore - çalışma zamanı-[Temel]. [alt]. [düzeltme]** | aspnetcore çalışma zamanı 2.1.0 | (6),[(7)]        | DotNet - çalışma zamanı-[Temel]. [alt]. [düzeltme]                    |
| DotNet - çalışma zamanı-[Temel]. [alt]                 | DotNet çalışma zamanı 2.1       |                  | DotNet - çalışma zamanı-[Temel]. [alt]. [son çalışma zamanı düzeltme]     |
| **DotNet - çalışma zamanı-[Temel]. [alt]. [düzeltme]**     | DotNet çalışma zamanı 2.1.0     | (5)              | ana bilgisayar fxr:\<çalışma zamanı sürümü > +                              |
| dotnet-host-fxr                                | dotnet-host-fxr          | (2)              | ana bilgisayar:\<çalışma zamanı sürümü > +                                  |
| DotNet ana bilgisayar                                    | DotNet ana bilgisayar              | (1),(8),(9),(10) |                                                           |

Düzeltme eki paketleri bir alternatifidir _sabitleme_ Paket Yöneticisi'ni kullanarak belirli bir sürüme paketler. Diğer uygulamalar/kullanıcıları etkileyen önlemek için bu tür uygulamalar yerleşik ve değiştirebilirsiniz bir kapsayıcıda dağıtılır.

## <a name="building-packages"></a>Yapı paketleri

https://github.com/dotnet/source-build Depo kaynağı tarball .NET Core SDK'sını ve tüm bileşenlerini derleme hakkında yönergeler sağlar. Kaynak derleme deposu çıktısı, bu makalenin ilk bölümünde açıklanan düzeni eşleşir.