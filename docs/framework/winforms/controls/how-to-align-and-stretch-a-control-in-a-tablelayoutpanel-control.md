---
title: 'Nasıl yapılır: TableLayoutPanel Denetiminde Bir Denetimi Hizalama ve Uzatma'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor.TLP.AlignStretchCtrl
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms], stretching controls
- controls [Windows Forms], stretching
- controls [Windows Forms], aligning
ms.assetid: 7dc1a157-6fee-4995-8ebc-b65bdc0909a8
ms.openlocfilehash: 06e152058337955164bd526e20e023d759340f01
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43504159"
---
# <a name="how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control"></a>Nasıl yapılır: TableLayoutPanel Denetiminde Bir Denetimi Hizalama ve Uzatma
Hizalama ve esnetme denetimlerinde bir <xref:System.Windows.Forms.TableLayoutPanel> ile <xref:System.Windows.Forms.Control.Anchor%2A> ve <xref:System.Windows.Forms.Control.Dock%2A> özellikleri.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-align-and-stretch-a-control"></a>Hizalama ve denetim Uzat  
  
1.  Sürükleme bir <xref:System.Windows.Forms.TableLayoutPanel> denetimi **araç kutusu** formunuza.  
  
2.  Sürükleme bir <xref:System.Windows.Forms.Button> denetimi **araç kutusu** sol üst hücresine <xref:System.Windows.Forms.TableLayoutPanel> denetimi. <xref:System.Windows.Forms.Button> Denetim hücrede ortalanır.  
  
3.  Değerini <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Anchor%2A> özelliğini `Left,Right`. <xref:System.Windows.Forms.Button> Denetim genişliği eşleşecek şekilde uzatır.  
  
4.  Değerini <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Anchor%2A> özelliğini `Top,Bottom`. <xref:System.Windows.Forms.Button> Denetim hücre yüksekliği eşleşecek şekilde uzatır.  
  
5.  Değerini <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Dock%2A> özelliğini <xref:System.Windows.Forms.DockStyle.Fill>. <xref:System.Windows.Forms.Button> Hücreyi dolduracak şekilde denetimi genişletir.  
  
6.  Değerini <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Dock%2A> özelliğini <xref:System.Windows.Forms.DockStyle.None>. <xref:System.Windows.Forms.Button> Denetimi tipini özgün boyutuna döner ve hücresinin sol üst köşeye taşır. **Windows Form Tasarımcısı** ayarladı <xref:System.Windows.Forms.Control.Anchor%2A> özelliğini `Top, Left`.  
  
7.  Değerini <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Anchor%2A> özelliğini `Bottom,Right`. <xref:System.Windows.Forms.Button> Denetimi hücrenin sağ alt köşeye taşır.  
  
8.  Değerini <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Anchor%2A> özelliğini <xref:System.Windows.Forms.AnchorStyles.None>. <xref:System.Windows.Forms.Button> Denetimi hücrenin merkezine taşır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [TableLayoutPanel Denetimi](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)
