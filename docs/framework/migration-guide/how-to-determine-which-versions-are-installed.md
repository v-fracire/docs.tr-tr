---
title: "Nasıl yapılır: hangi .NET Framework sürümlerinin yüklü olduğunu belirleme"
ms.date: 10/17/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
ms.custom: updateeachrelease
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining version
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: edd5a8e8cc32037d45d95d544f6eae5097d0c468
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a>Nasıl yapılır: Hangi .NET Framework Sürümlerinin Yüklü Olduğunu Belirleme
Kullanıcılar, yükleyin ve bilgisayarlarında birden çok .NET Framework sürümünü çalıştırın. Geliştirme ya da uygulamanızı dağıtma kullanıcının bilgisayarda hangi .NET Framework sürümlerinin yüklü olduğunu bilmeniz gerekebilir. .NET Framework sürümü tutulan ayrı ayrı olan iki ana bileşen içerdiğini unutmayın:  
  
-   Koleksiyon türleri ve uygulamalarınız için işlevselliği sağlayan kaynakları derlemeleri kümesi. .NET Framework ve derlemeleri aynı sürüm numarasına paylaşır.  
  
-   Yöneten ve uygulamanızın kodu yürütür ortak dil çalışma zamanı (CLR). CLR kendi sürüm numarasına göre tanımlanır (bkz [sürümleri ve bağımlılıkları](~/docs/framework/migration-guide/versions-and-dependencies.md)).  
  
 Bir bilgisayarda yüklü .NET Framework sürümleri doğru bir listesini almak için kayıt defterini görüntüleyebilir veya kod kayıt defterini sorgulayın:  
  
 [Kayıt defteri (sürümler 1-4) görüntüleme](#net_a)  
 [Kayıt defteri (sürüm 4.5 ve üstü) görüntüleme](#net_b)  
 [Kayıt defteri (sürümler 1-4) sorgulamak için kod kullanarak](#net_c)  
 [Kayıt defteri (sürüm 4.5 ve üstü) sorgulamak için kod kullanarak](#net_d)  
 [Kayıt defteri (sürüm 4.5 ve üstü) sorgulamak için PowerShell kullanma](#ps_a)  
  
 CLR sürümünü bulmak için bir araç veya kodu kullanabilirsiniz:  
  
 [Clrver Aracı'nı kullanma](#clr_a)  
 [System.Environment sınıfı sorgulamak için kod kullanarak](#clr_b)  
  
 .NET Framework'ün her sürüm için yüklü güncelleştirmeler algılama hakkında daha fazla bilgi için bkz: [nasıl yapılır: belirlemek, .NET Framework güncelleştirmeler yüklenir](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md). .NET Framework yükleme hakkında daha fazla bilgi için bkz: [geliştiriciler için .NET Framework'ü yüklemek](../../../docs/framework/install/guide-for-developers.md).  
  
<a name="net_a"></a>   
#### <a name="to-find-net-framework-versions-by-viewing-the-registry-net-framework-1-4"></a>.NET Framework sürümleri (.NET Framework 1-4) kayıt defteri görüntüleyerek bulmak için  
  
1.  Üzerinde **Başlat** menüsünde seçin **çalıştırmak**.  
  
2.  İçinde **açık** kutusuna **regedit.exe**.  
  
     regedit.exe'yi çalıştırmak için yönetici kimlik bilgileriniz olmalıdır.  
  
3.  Kayıt Defteri Düzenleyicisi'nde, aşağıdaki alt anahtarı açın:  
  
     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP`  
  
     Yüklenen sürümler NDP alt anahtarı altında listelenir. Sürüm numarasını depolanan **sürüm** girişi. İçin [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] **sürüm** giriştir istemci veya (altında NDP'nin), tam alt anahtarı altında veya her iki alt altında.  
  

    > [!NOTE]
    > Kayıt defterindeki "NET Framework Kurulum" klasörü, nokta karakteri ile başlamaz.

<a name="net_b"></a> 
#### <a name="to-find-net-framework-versions-by-viewing-the-registry-net-framework-45-and-later"></a>.NET Framework sürümleri (.NET Framework 4.5 ve üzeri) kayıt defteri görüntüleyerek bulmak için

1. Üzerinde **Başlat** menüsünde seçin **çalıştırmak**.

2. İçinde **açık** kutusuna **regedit.exe**.

     regedit.exe'yi çalıştırmak için yönetici kimlik bilgileriniz olmalıdır.

3. Kayıt Defteri Düzenleyicisi'nde, aşağıdaki alt anahtarı açın:

     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full`

     Unutmayın yoluna `Full` alt anahtarını içeren alt `Net Framework` yerine `.NET Framework`.

    > [!NOTE]
    > Varsa `Full` alt mevcut değil, ardından .NET Framework 4.5 yok veya sonraki bir sürümü yüklü.

     Adlı bir DWORD değeri için denetleyin. `Release`. Varlığını `Release` DWORD gösterir [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ya da daha yeni bu bilgisayara yüklendi.

     ![.NET Framework 4.5 için kayıt defteri girişi. ] (../../../docs/framework/migration-guide/media/clr-installdir.png "CLR_InstallDir")

     Değeri `Release` DWORD gösterir .NET Framework'ün hangi sürümünün yüklü.

    |Yayın DWORD değeri|Sürüm|
    |--------------------------------|-------------|
    |378389|.NET Framework 4.5|
    |378675|.NET framework 4.5.1 Windows 8.1 veya Windows Server 2012 R2 ile yüklenen|
    |378758|.NET framework 4.5.1 Windows 8, Windows 7 SP1 veya Windows Vista SP2 yüklü|
    |379893|.NET Framework 4.5.2|
    |Windows 10 sistemlerde: 393295<br /><br /> Diğer tüm işletim sistemi sürümlerinde: 393297|[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]|
    |Windows 10 Kasım güncelleştirme sistemlerde: 394254<br /><br /> Diğer tüm işletim sistemi sürümlerinde: 394271|[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]|
    |Windows 10 Anniversary Update: 394802<br /><br /> Diğer tüm işletim sistemi sürümlerinde: 394806|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]| 
    |Üzerinde Windows 10 oluşturucuları güncelleştirme: 460798<br/><br/> Diğer tüm işletim sistemi sürümlerinde: 460805 | .NET framework 4.7 |
    |Windows 10 kalan oluşturucuları güncelleştirme: 461308<br/><br/> Diğer tüm işletim sistemi sürümlerinde: 461310 | .NET framework 4.7.1 |
<a name="net_c"></a> 
#### <a name="to-find-net-framework-versions-by-querying-the-registry-in-code-net-framework-1-4"></a>.NET Framework sürümleri kod (.NET Framework 1-4) kayıt defterinde sorgulayarak bulmak için

- Kullanım <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> Windows kayıt defterinde HKEY_LOCAL_MACHINE altında Software\Microsoft\NET Framework Setup\NDP\ alt erişmek için sınıf.

     Aşağıdaki kod, bu sorgunun bir örneğini gösterir.

    > [!NOTE]
    > Bu kodu nasıl algılanacağını göstermez [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] veya sonraki bir sürümü. Denetleme `Release` önceki bölümde açıklandığı gibi bu sürümler algılamaya DWORD. Algılamıyor kodu için [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] veya sonraki sürümleri, bu makalenin sonraki bölümüne bakın.

     [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
     [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

     Örnekte aşağıdakine benzer bir çıktı oluşturulur:

    ```
    v2.0.50727  2.0.50727.4016  SP2
    v3.0  3.0.30729.4037  SP2
    v3.5  3.5.30729.01  SP1
    v4
      Client  4.0.30319
      Full  4.0.30319
    ```

<a name="net_d"></a> 
#### <a name="to-find-net-framework-versions-by-querying-the-registry-in-code-net-framework-45-and-later"></a>.NET Framework sürümleri kod (.NET Framework 4.5 ve üzeri) kayıt defterinde sorgulayarak bulmak için

1. Varlığını `Release` DWORD .NET Framework 4.5 veya sonraki bir bilgisayarda yüklü olduğunu gösterir. Anahtar değeri yüklü olan sürümü gösterir. Bu anahtar sözcük denetlemek için kullanın <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A> ve <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A> yöntemlerinin <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> Windows kayıt defterinde HKEY_LOCAL_MACHINE altında Software\Microsoft\NET Framework Setup\NDP\v4\Full alt erişmek için sınıf.

2. Değerini denetleyin `Release` yüklü olan sürümü belirlemek için anahtar sözcüğü. İleri uyumlu olması için tabloda listelenen değerleri eşit veya daha büyük bir değere denetleyebilirsiniz. .NET Framework sürümleri şunlardır ve ilişkili `Release` anahtar sözcükler.

    |Sürüm|Yayın DWORD değeri|
    |-------------|--------------------------------|
    |.NET Framework 4.5|378389|
    |.NET framework 4.5.1 Windows 8.1 ile yüklü|378675|
    |.NET framework 4.5.1 Windows 8, Windows 7 SP1 veya Windows Vista SP2 yüklü|378758|
    |.NET Framework 4.5.2|379893|
    |[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]Windows 10 ile yüklü|393295|
    |[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]diğer tüm Windows işletim sistemi sürümlerinde yüklü|393297|
    |[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]Windows 10 yüklü|394254|
    |[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]diğer tüm Windows işletim sistemi sürümlerinde yüklü|394271|
    |[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]Windows 10 Anniversary Update'te yüklü|394802|
    |[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]diğer tüm Windows işletim sistemi sürümlerinde yüklü|394806|
    |.NET framework Windows 10 oluşturucuları Update'te yüklü 4.7|460798|
    |.NET framework tüm diğer Windows işletim sistemi sürümleri yüklü 4.7|460805|
    |.NET framework Windows 10 sonbaharda oluşturucuları Update'te yüklü 4.7.1|461308|
    |.NET framework tüm diğer Windows işletim sistemi sürümleri yüklü 4.7.1|461310|

     Aşağıdaki örnek denetimleri `Release` belirlemek için kayıt defteri değerinde olup olmadığını [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] veya .NET Framework'ün daha yeni bir sürümü yüklü.

     [!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
     [!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

     Bu örnek, sürüm denetimi için önerilen yöntem aşağıda verilmiştir:

    - Denetlediği olup olmadığını değerini `Release` girişi *değerinden büyük veya eşit* bilinen yayın anahtarlarının değerini.

    - Eski sürümü için en son sürümüne sırayla denetler.

<a name="ps_a"></a> 
#### <a name="to-check-for-a-minimum-required-net-framework-version-by-querying-the-registry-in-powershell-net-framework-45-and-later"></a>PowerShell (.NET Framework 4.5 ve üzeri) kayıt defterinde sorgulayarak için gereken en düşük .NET Framework sürümü denetlemek için

- Aşağıdaki örnek değeri kontrol `Release` belirlemek için anahtar sözcüğü olup olmadığını .NET Framework 4.6.2 veya üstü yüklü, ne olursa olsun, Windows işletim sistemi sürümü (döndürme `True` etkinleştirilmişse ve `False` Aksi durumda).

    ```PowerShell
    Get-ChildItem "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\" | Get-ItemPropertyValue -Name Release | ForEach-Object { $_ -ge 394802 } 
    ```

    Değiştirebileceğiniz `394802` için farklı bir gereken en düşük .NET Framework sürüm denetlemek için aşağıdaki tabloda önceki örnekte başka bir değere sahip.
  
    |Sürüm|En düşük sürüm DWORD değeri|
    |-------------|--------------------------------|
    |.NET Framework 4.5|378389|
    |.NET Framework 4.5.1|378675|
    |.NET Framework 4.5.2|379893|
    |[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]|393295|
    |[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]|394254|
    |[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]|394802|
    |.NET framework 4.7|460798|
    |.NET framework 4.7.1|461308|
    
<a name="clr_a"></a> 
#### <a name="to-find-the-current-runtime-version-by-using-the-clrver-tool"></a>Geçerli çalışma zamanı sürümü Clrver Aracı'nı kullanarak bulma

- Bilgisayarda ortak dil çalışma zamanının hangi sürümlerinin yüklü olduğunu saptamak için CLR Sürüm Aracı'nı (Clrver.exe) kullanın.

     Visual Studio komut isteminden, girin `clrver`. Bu komut aşağıdakine benzer bir çıktı oluşturur:

    ```
    Versions installed on the machine:
    v2.0.50727
    v4.0.30319
    ```

     Bu aracı kullanmayla ilgili daha fazla bilgi için bkz: [Clrver.exe (CLR sürüm aracı)](~/docs/framework/tools/clrver-exe-clr-version-tool.md).

<a name="clr_b"></a> 
#### <a name="to-find-the-current-runtime-version-by-querying-the-environment-class-in-code"></a>Kod içinde Ortam sınıfını sorgulayarak geçerli çalışma zamanı sürümünü bulmak için

- Sorgu <xref:System.Environment.Version%2A?displayProperty=nameWithType> almak için özelliğini bir <xref:System.Version> kod şu anda yürütülmekte çalışma zamanı sürümü tanımlayan nesne. Kullanabileceğiniz <xref:System.Version.Major%2A?displayProperty=nameWithType> özelliği (örneğin, "4" sürüm 4.0 için), ana sürüm tanıtıcısını alın <xref:System.Version.Minor%2A?displayProperty=nameWithType> özelliği (örneğin, "0" sürüm 4.0 için), alt sürüm tanıtıcısını alın veya <xref:System.Object.ToString%2A?displayProperty=nameWithType> tüm sürümü almak için yöntemi dize ("aşağıdaki kodda gösterildiği gibi 4.0.30319.18010",). Bu özellik, kodu şu anda yürüten çalışma zamanı sürümünü gösteren tek bir değer döndürür; diğer sürümleri bilgisayarda yüklü çalışma zamanı derleme sürümleri döndürmez.

     .NET Framework sürüm 4, 4.5, 4.5.1 ve 4.5.2 <xref:System.Environment.Version%2A?displayProperty=nameWithType> özelliği döndürür bir <xref:System.Version> , dize gösterimi yok formun nesne `4.0.30319.xxxxx`. .NET Framework 4.6 ve daha sonra formun sahip `4.0.30319.42000`.

    > [!IMPORTANT]
    > İçin [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ve kullanarak daha sonra önermiyoruz <xref:System.Environment.Version%2A?displayProperty=nameWithType> çalışma zamanı sürümü algılamak için özellik. Bunun yerine, kayıt defterini sorgulayın açıklandığı şekilde öneririz [kod (.NET Framework 4.5 ve üzeri) kayıt defterinde sorgulayarak .NET Framework sürümlerini bulmak için](#net_d) bu makalenin önceki bölümünde.

     Sorgulama örneği <xref:System.Environment.Version%2A?displayProperty=nameWithType> özelliği çalışma zamanı sürüm bilgileri için:

     [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
     [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

     Örnekte aşağıdakine benzer bir çıktı oluşturulur:

    ```
    Version: 4.0.30319.18010
    ```

## <a name="see-also"></a>Ayrıca Bkz.
 [Nasıl yapılır: hangi .NET Framework güncelleştirmelerinin yüklü olduğunu belirleme](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)  
 [Geliştiriciler için .NET Framework'ü yükleme](../../../docs/framework/install/guide-for-developers.md)  
 [Sürümleri ve bağımlılıkları](~/docs/framework/migration-guide/versions-and-dependencies.md)