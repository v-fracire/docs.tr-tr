---
title: Denetim Türü Önerileri
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- user controls [Windows Forms], when to use
- custom controls [Windows Forms], types
- controls [Windows Forms], creating
ms.assetid: 5235fe9d-c36a-4c08-ae76-6cb90b50085e
ms.openlocfilehash: 5ce801a96bc4ef48934b983838dcf8578a5bc6e6
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43503023"
---
# <a name="control-type-recommendations"></a>Denetim Türü Önerileri
Geliştirin ve yeni denetimler uygulamak için güç .NET Framework sağlar. Alışık olduğunuz kullanıcı denetimine ek olarak, artık kendi boyama gerçekleştirmek ve devralma yoluyla mevcut denetimleri genişletmek bile mümkün olmayan özel denetimler yazabiliyor de bulabilirsiniz. Denetimi oluşturmak için hangi tür zorlanabilirsiniz. Bu bölümde içinden denetimlerin çeşitli türler arasında devralma işlemi yapabileceğini ve projeniz için seçmek için türü ile ilgili dikkat edilmesi gerekenler verir farklar vurgulanmaktadır.  
  
> [!NOTE]
>  Web formlarında kullanmak üzere bir denetim yazmak istiyorsanız [özel ASP.NET sunucu denetimleri geliştirme](https://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).  
  
## <a name="inheriting-from-a-windows-forms-control"></a>Devralmayı bir Windows Forms denetimi  
 Devralınan bir denetimi varolan herhangi bir Windows Forms denetimden türetebilirsiniz. Bu yaklaşım, tüm Windows Forms denetiminin devralınan işlevselliğini korumak ve ardından özel özellikler, yöntemler veya diğer işlevleri ekleyerek işlevselliği genişletmek için sağlar. Örneğin, türetilmiş bir denetim oluşturabilirsiniz <xref:System.Windows.Forms.TextBox> yalnızca sayı kabul edebilir ve bir değere dönüştürür giriş otomatik olarak. Bu tür bir denetim metin kutusundaki metin değiştirdiyseniz ve ek bir özellik sahip olduğunda çağrılan bir doğrulama kodu içerebilir değeri. Bazı denetimler de özel görünüşünü denetiminizin grafik arabirimine geçersiz kılarak ekleyebilirsiniz <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi temel sınıf.  
  
 Bir Windows Forms denetimi devralır:  
  
-   İhtiyacınız olan işlevleri çoğunu zaten varolan bir Windows Forms denetimi aynı.  
  
-   Yeni bir grafik ön uç için varolan bir denetimi tasarım istediğiniz veya özel bir grafik arabirim gerekmez.  
  
## <a name="inheriting-from-the-usercontrol-class"></a>UserControl sınıfından devralma  
 Bir kullanıcı denetimi, Windows Forms denetimleri ortak bir kapsayıcıya kapsüllenmiş koleksiyonudur. Kapsayıcı tüm her Windows Forms denetimleri ilişkilendirilmiş devralınan işlevselliğini içerir ve seçmeli olarak kullanıma sunmak ve bunların özelliklerini bağlama olanak tanır. Bir kullanıcı denetimi örneği veritabanından müşteri adresi verilerini görüntülemek üzere tasarlanmış bir denetimi olabilir. Bu denetim, her alanı ve düğme denetimleri Kayıtlarda gezinmek için görüntülenecek birkaç metin kutuları verilebilir. Veri bağlama özellikleri seçmeli olarak sunulabilir ve tüm denetim paketlenmeli ve uygulamadan uygulamaya yeniden kullanılabilir.  
  
 Devralınan <xref:System.Windows.Forms.UserControl> , sınıf:  
  
-   Çeşitli Windows Forms denetimleri işlevlerini tek bir yeniden kullanılabilir biriminde birleştirmek istediğiniz.  
  
## <a name="inheriting-from-the-control-class"></a>Denetim sınıfından devralma  
 Sıfırdan büyük ölçüde devralarak oluşturmak için bir denetim oluşturmak için başka bir yolu olan <xref:System.Windows.Forms.Control>. <xref:System.Windows.Forms.Control> Sınıfın tüm temel işlevleri (örneğin, olayları) denetimleri tarafından gerekli ancak hiçbir özel denetim işlevleri veya grafik arabirim sağlar. Bir denetimi devralarak oluşturma <xref:System.Windows.Forms.Control> sınıfı daha birçok düşünce ve kullanıcı denetimi ya da mevcut bir Windows Forms denetimi devralan daha çaba gerektirir. Yazar için kod yazmanız gereken <xref:System.Windows.Forms.Control.OnPaint%2A> gerekli işlevselliği belirli kod yanı sıra denetim olayı. Daha fazla esneklik, ancak izin verilir ve özel uyarlama bir denetim tam ihtiyaçlarınıza uyacak şekilde kurtarabilirsiniz. Örnek bir özel denetimin görünümünü ve bir analog saat eylemi yineleme saati denetimidir. Özel boyama yanıt olarak taşımak için saat kullanımına neden çağrılacak <xref:System.Windows.Forms.Timer.Tick> olayları iç zamanlayıcı bileşeni.  
  
 Devralınan <xref:System.Windows.Forms.Control> , sınıf:  
  
-   Özel bir grafik gösterimi denetiminizin sunmak istiyorsunuz.  
  
-   Standart denetimler kullanılabilir olmayan özel işlevselliği uygulamak gerekir.  
  
-   [Nasıl yapılır: Araç Kutusu Öğelerini Seç İletişim Kutusunda bir Denetimi Görüntüleme](https://msdn.microsoft.com/library/9yxtkx75\(v=vs.110\))  
  
-   [İzlenecek yol: DesignerSerializationVisibilityAttribute ile Standart Türler Koleksiyonlarının Seri Hale Getirilmesi](serializing-collections-designerserializationvisibilityattribute.md)  
  
-   [İzlenecek yol: Visual C# ile beraber Windows Forms Denetimi'nden Devralma](https://msdn.microsoft.com/library/5h0k2e6x\(v=vs.110\))  
  
-   [Nasıl yapılır: Bir Denetim için Araç Kutusu Bit Eşlemi Sağlama](https://msdn.microsoft.com/library/4wk1wc0a\(v=vs.110\))  
  
-   [Nasıl yapılır: Mevcut Windows Forms Denetimlerinden Devralma](https://msdn.microsoft.com/library/7h62478z\(v=vs.110\))  
  
-   [İzlenecek yol: Tasarım Zamanında Özel Windows Forms Denetimleri Hatalarını Ayıklama](https://msdn.microsoft.com/library/5ytx0z24\(v=vs.110\))  
  
-   [Nasıl yapılır: Denetim Sınıfından Devralma](https://msdn.microsoft.com/library/skcysbt2\(v=vs.110\))  
  
-   [Nasıl yapılır: Bir UserControl Denetiminin Çalışma Zamanı Davranışını Sınama](how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
  
-   [Nasıl yapılır: Tasarım Zamanında Denetimi Formların Kenarlarına Hizalama](https://msdn.microsoft.com/library/1fxyb15b\(v=vs.110\))  
  
-   [Nasıl yapılır: UserControl Sınıfından Devralma](https://msdn.microsoft.com/library/00ctb4z0\(v=vs.110\))  
  
-   [Nasıl yapılır: Windows Forms için Denetimler Yazma](https://msdn.microsoft.com/library/bs3yhkh7\(v=vs.110\))  
  
-   [Nasıl yapılır: Bileşik Denetimler Yazma](https://msdn.microsoft.com/library/3sf86w5h\(v=vs.110\))  
  
-   [İzlenecek yol: Visual Basic İle Bileşik Denetim Yazma](https://msdn.microsoft.com/library/c316f119\(v=vs.110\))  
  
-   [İzlenecek yol: Visual C# İle Bileşik Denetim Yazma](https://msdn.microsoft.com/library/a6h7e207\(v=vs.110\))  
  
-   [İzlenecek yol: Visual Basic ile beraber Windows Forms Denetimi'nden Devralma](https://msdn.microsoft.com/library/w2a8y03d\(v=vs.110\))  
  
-   [Nasıl yapılır: tasarım zamanı özelliklerinden faydalanan Windows Forms denetimi oluşturma](https://msdn.microsoft.com/library/307hck25\(v=vs.110\))  
  
-   [Nasıl yapılır: tasarım zamanı özelliklerinden faydalanan Windows Forms denetimi oluşturma](https://msdn.microsoft.com/library/307hck25\(v=vs.120\))  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Basit Bir Windows Forms Denetimi Geliştirme](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md)  
 [Özel Denetim Çeşitleri](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
