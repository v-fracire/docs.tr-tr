---
title: 'Nasıl yapılır: Devralma Seçici İletişim Kutusunu Kullanarak Form Devralma'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], forms
- Inheritance Picker dialog box
- inherited forms [Windows Forms], creating
ms.assetid: 969b4c04-12aa-4297-93a2-0ae747447823
ms.openlocfilehash: 5bcd29531858f9cf014042db7ee447cecfdd89b1
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43525750"
---
# <a name="how-to-inherit-forms-using-the-inheritance-picker-dialog-box"></a>Nasıl yapılır: Devralma Seçici İletişim Kutusunu Kullanarak Form Devralma
Bir form veya diğer nesne devral en kolay yolu kullanmaktır **devralma Seçici** iletişim kutusu. Bununla, diğer çözümlere önceden oluşturduğunuz kodu veya kullanıcı arabirimi (UI) avantajlarından yararlanabilirsiniz.  
  
> [!NOTE]
>  Bir form devralma için **devralma Seçici** iletişim kutusunda, bu formu içeren proje gerekir oluşturulan bir yürütülebilir dosya veya DLL. Projeyi oluşturmak için Seç **Çözümü Derle** gelen **derleme** menüsü.  
>   
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-create-a-windows-form-inherited-from-an-existing-form-by-using-the-inheritance-picker"></a>Devralma Seçici'yi kullanarak varolan bir formdan devralınan bir Windows formu oluşturma  
  
1.  Gelen **proje** menüsünde seçin **Windows formu eklemek**.  
  
     **Yeni Öğe Ekle** iletişim kutusu açılır.  
  
2.  Seçin **devralınan Form** şablonunu ve bunun içinde ad **adı** kutusu. Tıklayın **Ekle** devam etmek için düğmesine.  
  
     **Devralma Seçici** iletişim kutusu açılır. Geçerli proje forms içeriyorsa, bunlar görüntülenir **devralma Seçici** iletişim kutusu.  
  
3.  Bir formdan başka bir derlemede devralmak için tıklatın **Gözat** düğmesi.  
  
4.  İçinde **devralınacak bir bileşen içeren bir dosya seçin** iletişim kutusunda, istediğiniz modülü ve formu içeren projeye gidin.  
  
5.  Onu seçin ve .exe veya .dll dosyası adına **açık** düğmesi.  
  
     Bu size döndürür **devralma Seçici** iletişim kutusu, burada bileşen artık listelenir, yanı sıra, bulunduğu proje.  
  
6.  Bileşeni seçin.  
  
     İçinde **Çözüm Gezgini**, bileşen projenize eklenir. Bir kullanıcı Arabirimi varsa, devralınmış bir form parçası olan denetimler bir simge ile işaretlenir (![VisualBasicInheritanceSymbol ekran](../../../../docs/framework/winforms/advanced/media/vbinheritanceglyph.gif "vbInheritanceGlyph")), ve seçili olduğunda, belirten bir kenarlık üst sınıf formda bir denetim olan güvenlik düzeyi. Aşağıdaki tabloda farklı güvenlik düzeylerine karşılık gelen davranışlar listelenmektedir.  
  
    |Denetim için güvenlik düzeyi|Kullanılabilir etkileşiminin Tasarımcısı ve form devralınmış Kod Düzenleyicisi|  
    |-------------------------------|--------------------------------------------------------------------------------|  
    |Ortak|Boyutlandırma tutamaçları ile standart kenarlık: denetim boyutlandırıldığından ve taşındı. Denetim, dahili olarak onu bildiren sınıfın ve harici olarak diğer sınıflar tarafından erişilebilir.|  
    |Korumalı|Boyutlandırma tutamaçları ile standart kenarlık: denetim boyutlandırıldığından ve taşındı. Dahili olarak onu bildiren sınıfın ve üst sınıfından devralır, ancak dış sınıfları tarafından erişilemez herhangi bir sınıf tarafından erişilebilir.|  
    |İç (korumalı Visual Basic'te Friend) korumalı|Boyutlandırma tutamaçları ile standart kenarlık: denetim boyutlandırıldığından ve taşındı. Dahili olarak onu bildiren sınıfın, üst sınıfından devralan herhangi bir sınıf ve onu içeren derlemenin genel diğer üyeleri tarafından erişilebilir.|  
    |İç (Visual Basic'te Friend)|Standart Özellikler görünür formunda gösterilen hiçbir boyutlandırma tutamaçlarını kenarlıklı **özellikleri** penceresi. Ancak, tüm yönlerini denetimi salt okunur kabul edilir. Taşıyamaz veya denetimin boyutunu veya özelliklerini değiştirin. Denetim bir grup kutusu gibi diğer denetim kapsayıcısı ise yeni denetimler eklenemez ve bu denetimleri ortak bile mevcut denetimleri kaldırılamaz. Denetim, yalnızca derlemenin içerdiği diğer üyeleri tarafından erişilebilir.|  
    |Özel|Standart Özellikler görünür formunda gösterilen hiçbir boyutlandırma tutamaçlarını kenarlıklı **özellikleri** penceresi. Ancak, tüm yönlerini denetimi salt okunur kabul edilir. Taşıyamaz veya denetimin boyutunu veya özelliklerini değiştirin. Denetim bir grup kutusu gibi diğer denetim kapsayıcısı ise yeni denetimler eklenemez ve bu denetimleri ortak bile mevcut denetimleri kaldırılamaz. Denetim yalnızca bunu bildiren bir sınıf tarafından erişilebilir.|  
  
     Taban formun görünüşünü değiştirme hakkında daha fazla bilgi için bkz: [taban formun görünüşünü değiştirmenin etkileri](../../../../docs/framework/winforms/advanced/effects-of-modifying-base-form-appearance.md).  
  
    > [!NOTE]
    >  Standart denetimler ve Windows Forms bileşenleri ile devralınan denetimler ve bileşenler birleştirdiğinizde çakışmaları z-sıralamasıyla ile karşılaşabilirsiniz. Z-tıklayarak yapılır sırasını değiştirerek bunu düzeltebilirsiniz **biçimi** işaret menüsünde **sipariş**ve ardından **öne** veya  **Arkaya Gönder**. Denetimleri z düzeni hakkında daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms'da nesneleri katman](../../../../docs/framework/winforms/controls/how-to-layer-objects-on-windows-forms.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Inherits Deyimi](~/docs/visual-basic/language-reference/statements/inherits-statement.md)  
 [using](~/docs/csharp/language-reference/keywords/using.md)  
 [Taban Formun Görünüşünü Değiştirmenin Etkileri](../../../../docs/framework/winforms/advanced/effects-of-modifying-base-form-appearance.md)  
 [Windows Forms Görsel Devralma](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)
