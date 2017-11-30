---
title: "Nasıl yapılır: Windows Formlarına Kullanıcı Arabirimi Olmadan Denetimler Ekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
f1_keywords: NonVisualSelection
helpviewer_keywords:
- invisible controls [Windows Forms]
- Windows Forms controls, adding to form
- controls [Windows Forms], nonvisual
- Windows Forms controls, nonvisual
- nonvisual controls [Windows Forms]
ms.assetid: 52134d9c-cff6-4eed-8e2b-3d5eb3bd494e
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7deea3aca390ebfa4cc1fcbf16a0e898301ae434
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-controls-without-a-user-interface-to-windows-forms"></a>Nasıl yapılır: Windows Formlarına Kullanıcı Arabirimi Olmadan Denetimler Ekleme
Görsel olmayan denetim (veya bileşen) uygulamanız için işlevsellik sağlar. Diğer denetimleri farklı bileşenleri bir kullanıcı arabirimi kullanıcıya sağlamaz ve dolayısıyla Windows Form Tasarımcısı yüzey üzerinde görüntülenmesi gerekmez. Bir bileşen bir forma eklendiğinde, Windows Form Tasarımcısı yeniden boyutlandırılabilir Tepsisi tüm bileşenleri görüntülendiği formun alt kısmındaki görüntüler. Bir denetim için bileşen Tepsisi eklendikten sonra bileşeni seçin ve form üzerinde herhangi bir denetimi gibi özellikleri ayarlayın.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-add-a-component-to-a-windows-form"></a>Bir Windows formu bir bileşen eklemek için  
  
1.  Formu açın. Ayrıntılar için bkz [nasıl yapılır: görüntü Windows Forms Tasarımcısı'nda](http://msdn.microsoft.com/en-us/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5).  
  
2.  İçinde **araç**, bir bileşeni tıklatın ve formunuza sürükleyin.  
  
     Bileşeniniz bileşen tepsisinde görünür.  
  
 Ayrıca, bileşenleri, çalışma zamanında bir forma eklenebilir. Özellikle bileşenleri bir kullanıcı arabirimine sahip denetimleri farklı bir görsel ifade olmadığı için yaygın bir senaryo budur. Aşağıdaki örnekte bir <xref:System.Windows.Forms.Timer> bileşen çalışma zamanında eklenir. (Unutmayın [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] farklı zamanlayıcılar sayısını içerir; bu durumda, bir Windows Forms kullanın <xref:System.Windows.Forms.Timer> bileşeni. Farklı zamanlayıcılar hakkında daha fazla bilgi için [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], bkz: [sunucu tabanlı zamanlayıcılar giriş](http://msdn.microsoft.com/en-us/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).)  
  
> [!CAUTION]
>  Bileşenleri genellikle etkili bir şekilde çalışması bileşeni için ayarlanmalıdır denetim özgü özellikleri vardır. Durumunda <xref:System.Windows.Forms.Timer> aşağıdaki bileşeni, ayarladığınız `Interval` özelliği. Bileşenlerin özellikleri bu bileşen için gerekli ayarlayın projenize eklerken emin olun.  
  
#### <a name="to-add-a-component-to-a-windows-form-programmatically"></a>Bir bileşen için Windows formu programlı olarak eklemek için  
  
1.  Bir örneğini oluşturmak <xref:System.Windows.Forms.Timer> kodda sınıfı.  
  
2.  Ayarlama `Interval` Zamanlayıcı çizgilerine arasındaki süreyi belirlemek için özellik.  
  
3.  Bileşeniniz için gerekli diğer özellikleri yapılandırın.  
  
     Aşağıdaki kod oluşturulmasını gösterir bir <xref:System.Windows.Forms.Timer> ile kendi `Interval` özellik kümesi.  
  
    ```vb  
    Public Sub CreateTimer()  
       Dim timerKeepTrack As New System.Windows.Forms.Timer  
       timerKeepTrack.Interval = 1000  
    End Sub  
    ```  
  
    ```csharp  
    public void createTimer()  
    {  
       System.Windows.Forms.Timer timerKeepTrack = new  
           System.Windows.Forms.Timer();  
       timerKeepTrack.Interval = 1000;  
    }  
    ```  
  
    ```cpp  
    public:  
       void createTimer()  
       {  
          System::Windows::Forms::Timer^ timerKeepTrack = gcnew  
             System::Windows::Forms::Timer();  
          timerKeepTrack->Interval = 1000;  
       }  
    ```  
  
    > [!IMPORTANT]
    >  Yerel bir güvenlik riski ağ üzerinden bilgisayarınıza kötü amaçlı bir UserControl başvurarak doğurabilir. Bu, yalnızca, yanlışlıkla projenize ekleme ve ardından zararlı olabilecek özel bir denetim oluşturma kötü niyetli bir kişi olması durumunda ilgili bir sorun olabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Forms denetimleri](../../../../docs/framework/winforms/controls/index.md)  
 [Nasıl yapılır: Windows formlarına denetimler ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)  
 [Nasıl yapılır: Windows formlarına ActiveX denetimleri ekleme](../../../../docs/framework/winforms/controls/how-to-add-activex-controls-to-windows-forms.md)  
 [Nasıl yapılır: Windows Formları arasında denetimleri kopyalama](../../../../docs/framework/winforms/controls/how-to-copy-controls-between-windows-forms.md)  
 [Windows formlarına denetimler koyma](../../../../docs/framework/winforms/controls/putting-controls-on-windows-forms.md)  
 [Ayrı Windows Forms denetimlerini etiketleme ve kısayollarını sunma](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [Windows Forms'ta kullanılacak denetimler](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [Windows Forms denetimleri işlevi](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)