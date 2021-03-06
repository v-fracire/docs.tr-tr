---
title: 'Nasıl yapılır: Tasarımcı Kullanarak bir ToolBar Denetimine Düğme Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding separators
- examples [Windows Forms], toolbars
- ToolBar control [Windows Forms], adding drop-down menus
ms.assetid: d9ce3040-3e21-4e2d-80ae-b430982b2db8
ms.openlocfilehash: b96f112c83d2296356e3eb566a24315bcefeff1f
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44253175"
---
# <a name="how-to-add-buttons-to-a-toolbar-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak bir ToolBar Denetimine Düğme Ekleme
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip> Denetimi değiştirir ve işlevsellik ekler <xref:System.Windows.Forms.ToolBar> denetler; ancak, <xref:System.Windows.Forms.ToolBar> denetim korunur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz.  
  
 En önemli parçalarından biri <xref:System.Windows.Forms.ToolBar> ona eklediğiniz düğmeler denetimidir. Bunlar, menü komutlarını kolay erişim sağlamak için kullanılabilir veya alternatif olarak, bunlar başka bir alanda komutları menüsü yapısı içinde kullanılabilir değil, kullanıcılarınıza göstermek için uygulamanızın kullanıcı arabiriminin yerleştirilebilir.  
  
 Aşağıdaki yordam gerektirir bir **Windows uygulama** proje içeren bir form içeren bir <xref:System.Windows.Forms.ToolBar> denetimi. Bu tür bir proje ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir Windows uygulaması projesi oluşturmak](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) ve [nasıl yapılır: Windows Forms denetimlerine ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-add-buttons-at-design-time"></a>Tasarım zamanında düğme eklemek için  
  
1.  Seçin <xref:System.Windows.Forms.ToolBar> denetimi.  
  
2.  İçinde **özellikleri** penceresinde tıklayın <xref:System.Windows.Forms.ToolBar.Buttons%2A> özelliğini seçin ve **üç nokta** (![VisualStudioEllipsesButton ekran](../../../../docs/framework/winforms/media/vbellipsesbutton.png " vbEllipsesButton")) açmak için düğmeyi **ToolBarButton Koleksiyonu Düzenleyicisi**.  
  
3.  Kullanım **Ekle** ve **Kaldır** düğmeleri ekleme ve kaldırma düğmelerden <xref:System.Windows.Forms.ToolBar> denetimi.  
  
4.  Configure the properties of düğmelerin **özellikleri** Düzenleyicisinin sağ taraftaki bölmede görüntülenen penceresi. Aşağıdaki tabloda, dikkate alınması gereken bazı önemli özellikleri gösterir.  
  
    |Özellik|Açıklama|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A>|Menü açılan araç çubuğu düğmesini görüntülenecek ayarlar. Araç çubuğu düğmesinin <xref:System.Windows.Forms.ToolBarButton.Style%2A> özelliği ayarlanmalıdır <xref:System.Windows.Forms.ToolBarButtonStyle.DropDownButton>. Bu özellik bir örneğini alır <xref:System.Windows.Forms.ContextMenu> sınıfı başvuru olarak.|  
    |<xref:System.Windows.Forms.ToolBarButton.PartialPush%2A>|Geçiş stili araç çubuğu düğmesi kısmen gönderildiğinde olup olmadığını belirler. Araç çubuğu düğmesinin <xref:System.Windows.Forms.ToolBarButton.Style%2A> özelliği ayarlanmalıdır <xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton>.|  
    |<xref:System.Windows.Forms.ToolBarButton.Pushed%2A>|Geçiş stili araç çubuğu düğmesi şu anda zorlanan durumda olup olmadığını belirler. Araç çubuğu düğmesinin <xref:System.Windows.Forms.ToolBarButton.Style%2A> özelliği ayarlanmalıdır <xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton> veya <xref:System.Windows.Forms.ToolBarButtonStyle.PushButton>.|  
    |<xref:System.Windows.Forms.ToolBarButton.Style%2A>|Araç çubuğu düğmesini stilini ayarlar. Değerlerde biri olmalıdır <xref:System.Windows.Forms.ToolBarButtonStyle> sabit listesi.|  
    |<xref:System.Windows.Forms.ToolBarButton.Text%2A>|Düğme tarafından görüntülenen metin dizesi.|  
    |<xref:System.Windows.Forms.ToolBarButton.ToolTipText%2A>|Düğmenin araç ipucu olarak görünen metin.|  
  
5.  Tıklayın **Tamam** iletişim kutusunu kapatmak ve belirttiğiniz paneller oluşturun.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ToolBar>  
 [Nasıl yapılır: ToolBar Düğmesi için Simge Tanımlama](../../../../docs/framework/winforms/controls/how-to-define-an-icon-for-a-toolbar-button.md)  
 [Nasıl yapılır: Araç Çubuğu Düğmeleri için Menü Olaylarını Tetikleme](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)  
 [ToolBar Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/toolbar-control-overview-windows-forms.md)  
 [ToolBar Denetimi](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)
