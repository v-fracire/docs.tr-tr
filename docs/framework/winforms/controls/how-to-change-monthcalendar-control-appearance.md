---
title: 'Nasıl yapılır: Windows Forms MonthCalendar denetimi değiştirme&#39;görünümünü'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], calendar controls
- MonthCalendar control [Windows Forms], formatting display
ms.assetid: d09b95c9-e108-4608-9b31-b9100c0677bf
ms.openlocfilehash: 4f91363764099cabfa1a7939ff07e627aeb6c815
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43802021"
---
# <a name="how-to-change-the-windows-forms-monthcalendar-control39s-appearance"></a>Nasıl yapılır: Windows Forms MonthCalendar denetimi değiştirme&#39;görünümünü
Windows Forms <xref:System.Windows.Forms.MonthCalendar> denetimi birçok yönden Takvim görünümünü özelleştirmenize olanak sağlar. Örneğin, bir renk şeması ayarlayın ve hafta sayıları ve geçerli tarih görüntülemek veya gizlemek seçin.  
  
### <a name="to-change-the-month-calendars-color-scheme"></a>Ay takvim renk düzenini değiştirmek için  
  
-   Özellikleri ayarlamak <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A> ve <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>. <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A> Özelliği için haftanın günlerini de yazı tipi rengini belirler. <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> Özelliği koyun ve görüntülenen ayı veya ay izleyen tarihleri rengini belirler.  
  
    ```vb  
    MonthCalendar1.TitleBackColor = System.Drawing.Color.Blue  
    MonthCalendar1.TrailingForeColor = System.Drawing.Color.Red  
    MonthCalendar1.TitleForeColor = System.Drawing.Color.Yellow  
    ```  
  
    ```csharp  
    monthCalendar1.TitleBackColor = System.Drawing.Color.Blue;  
    monthCalendar1.TrailingForeColor = System.Drawing.Color.Red;  
    monthCalendar1.TitleForeColor = System.Drawing.Color.Yellow;  
    ```  
  
    ```cpp  
    monthCalendar1->TitleBackColor = System::Drawing::Color::Blue;  
    monthCalendar1->TrailingForeColor = System::Drawing::Color::Red;  
    monthCalendar1->TitleForeColor = System::Drawing::Color::Yellow;  
    ```  
  
    > [!NOTE]
    >  Tema bağlı olarak Windows Vista ile başlayarak, bazı özellikleri ayarlama Takvim görünümünü değişmeyebilir. Örneğin, Windows Aero teması kullanmak üzere ayarlanmışsa ayarlamak <xref:System.Windows.Forms.MonthCalendar.BackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>, veya <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> özellikleri etkisizdir. Takvim güncelleştirilmiş bir sürümünü geçerli işletim sistemi temayı çalışma zamanında türetilmiş bir görünümle işlenen olmasıdır. Bu özellikleri kullanmak ve Takvim önceki sürümünü etkinleştirmek istiyorsanız, uygulamanız için görsel stil devre dışı bırakabilirsiniz. Görsel stiller devre dışı bırakma, görünümünü ve davranışını uygulamanızdaki diğer denetimlerin etkileyebilir. Visual Basic'te görsel stiller devre dışı bırakmak için Proje Tasarımcısı'nı açın ve işaretini kaldırın **etkinleştirme XP görsel stilleri** onay kutusu. C# görsel stiller devre dışı bırakmak için program.cs dosyasını açın ve açıklama `Application.EnableVisualStyles();`. Görsel stiller hakkında daha fazla bilgi için bkz: [nasıl yapılır: Windows XP görsel stilleri etkinleştirme](https://msdn.microsoft.com/library/0a038ade-31cf-4e56-9cfe-7a1e6b83b57f).  
  
### <a name="to-display-the-current-date-at-the-bottom-of-the-control"></a>Geçerli bir tarih denetiminin altındaki görüntülemek için  
  
-   Ayarlama <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> özelliğini `true`. Aşağıdaki örnekte, görüntüleme ve ne zaman formun çift tıklandığında bugünün tarihini atlama arasında geçiş yapar.  
  
    ```vb  
    Private Sub Form1_DoubleClick(ByVal sender As Object, _  
    ByVal e As System.EventArgs) Handles MyBase.DoubleClick  
       ' Toggle between True and False.  
       MonthCalendar1.ShowToday = Not MonthCalendar1.ShowToday  
    End Sub  
    ```  
  
    ```csharp  
    private void Form1_DoubleClick(object sender, System.EventArgs e)  
    {  
       // Toggle between True and False.  
       monthCalendar1.ShowToday = !monthCalendar1.ShowToday;  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void Form1_DoubleClick(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          // Toggle between True and False.  
          monthCalendar1->ShowToday = !monthCalendar1->ShowToday;  
       }  
    ```  
  
     (Visual C# [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) formun oluşturucuda olay işleyicisi kaydetmek için aşağıdaki kodu yerleştirin.  
  
    ```csharp  
    this.DoubleClick += new System.EventHandler(this.Form1_DoubleClick);  
    ```  
  
    ```cpp  
    this->DoubleClick += gcnew System::EventHandler(this,  
       &Form1::Form1_DoubleClick);  
    ```  
  
### <a name="to-display-week-numbers"></a>Hafta sayıları görüntülemek için  
  
-   Ayarlama <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> özelliğini `true`. Bu özellik, kod veya Özellikler penceresinde ayarlayabilirsiniz.  
  
     Hafta sayıları haftanın ilk günü solundaki ayrı bir sütunda görüntülenir.  
  
    ```vb  
    MonthCalendar1.ShowWeekNumbers = True  
    ```  
  
    ```csharp  
    monthCalendar1.ShowWeekNumbers = true;  
    ```  
  
    ```cpp  
    monthCalendar1->ShowWeekNumbers = true;  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [MonthCalendar Denetimi](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)  
 [Nasıl yapılır: Windows Forms MonthCalendar Denetiminde Tarih Aralığı Seçme](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)  
 [Nasıl yapılır: Windows Forms MonthCalendar Denetimi ile Belirli Günleri Kalın Olarak Görüntüleme](../../../../docs/framework/winforms/controls/display-specific-days-in-bold-with-wf-monthcalendar-control.md)  
 [Nasıl yapılır: Windows Forms MonthCalendar Denetiminde Birden Fazla Ay Görüntüleme](../../../../docs/framework/winforms/controls/display-more-than-one-month-wf-monthcalendar-control.md)
