---
title: 'Nasıl yapılır: Bir Windows Forms Düğmesini Kabul Et Düğmesi Olarak Belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- buttons [Windows Forms], default on Windows Forms
- Accept button on Windows Forms
- Button control [Windows Forms], designating as default
- Windows Forms controls, default button on form
ms.assetid: 22cc9da6-b913-4e04-9554-dee443ac5c3a
ms.openlocfilehash: a69964b83e9948a844483725616a150234a38c97
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531946"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button"></a>Nasıl yapılır: Bir Windows Forms Düğmesini Kabul Et Düğmesi Olarak Belirtme
Herhangi bir Windows formunda tanımladığınız bir <xref:System.Windows.Forms.Button> kabul et düğmesi olarak da bilinen varsayılan düğme olarak denetim. Her kullanıcı ENTER tuşuna bastığında, bağımsız olarak form üzerindeki diğer denetim odağı olan varsayılan düğme tıklatıldığında.  
  
> [!NOTE]
>  Başka bir düğme denetimi odağa sahip olduğunda bu öğeler için özel durumlar — odaklanılan düğmesine tıklandığında bu durumda, — veya çok satırlı metin kutusu veya ENTER tuşuna yakalar özel bir denetim.  
  
### <a name="to-designate-the-accept-button"></a>Kabul Et düğmesi atamak için  
  
1.  Formun <xref:System.Windows.Forms.Form.AcceptButton%2A> özelliğine uygun <xref:System.Windows.Forms.Button> denetim.  
  
    ```vb  
    Private Sub SetDefault(ByVal myDefaultBtn As Button)  
      Me.AcceptButton = myDefaultBtn   
    End Sub  
    ```  
  
    ```csharp  
    private void SetDefault(Button myDefaultBtn)  
    {  
       this.AcceptButton = myDefaultBtn;  
    }  
    ```  
  
    ```cpp  
    private:  
       void SetDefault(Button ^ myDefaultBtn)  
       {  
          this->AcceptButton = myDefaultBtn;  
       }  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Form.AcceptButton%2A>  
 [Düğme Kontrolüne Genel Bakış](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [Windows Forms Düğme Kontrolü Seçme Yolları](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [Nasıl yapılır: Windows Forms Düğme Tıklamalarına Yanıt Verme](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [Nasıl yapılır: Bir Windows Forms Düğmesini İptal Düğmesi Olarak Belirtme](../../../../docs/framework/winforms/controls/how-to-designate-a-windows-forms-button-as-the-cancel-button.md)  
 [Düğme Kontrolü](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
