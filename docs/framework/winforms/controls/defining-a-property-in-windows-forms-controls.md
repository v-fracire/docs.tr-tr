---
title: Windows Forms Denetimlerinde Özellik Tanımlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties [Windows Forms], defining in code
- custom controls [Windows Forms], defining properties in code
ms.assetid: c2eb8277-a842-4d99-89a9-647b901a0434
ms.openlocfilehash: c21aee867fc78c55e62eb183bb1a12ebf1c472e8
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43858672"
---
# <a name="defining-a-property-in-windows-forms-controls"></a>Windows Forms Denetimlerinde Özellik Tanımlama
Özellikleri genel bakış için bkz. [özelliklerine genel bakış](https://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52). Bir özellik tanımlarken birkaç önemli nokta vardır:  
  
-   Özellikleri için tanımladığınız öznitelikleri uygulamanız gerekir. Bir özellik Tasarımcısı'nı nasıl görüntülenmelidir öznitelikleri belirtin. Ayrıntılar için bkz [bileşenler için tasarım zamanı öznitelikleri](https://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3).  
  
-   Özelliği değiştirmeyi denetimin görünümünü etkiler, çağrı <xref:System.Windows.Forms.Control.Invalidate%2A> yöntemi (denetiminiz devralınan <xref:System.Windows.Forms.Control>) öğesinden `set` erişimcisi. <xref:System.Windows.Forms.Control.Invalidate%2A> sırayla çağırır <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi denetimi yeniden çizer. Birden çok çağrılar <xref:System.Windows.Forms.Control.Invalidate%2A> sonucu tek bir çağrıda <xref:System.Windows.Forms.Control.OnPaint%2A> verimlilik için.  
  
-   .NET Framework sınıf kitaplığı, tamsayı, ondalık sayılar, Boole değerleri ve diğerleri gibi ortak veri türleri için tür dönüştürücüleri sağlar. Genellikle amacı bir tür dönüştürücüsü, dize değeri dönüştürme (gelen dize verileri diğer veri türleri için) sağlamaktır. Ortak veri türleri, değerleri dizeler ve uygun veri türlerini dizelere dönüştürme varsayılan tür dönüştürücüleri ile ilişkilidir. Özel bir özellik tanımlarsanız (diğer bir deyişle, standart dışı) veri türü, bu özellik ile ilişkilendirilecek tür dönüştürücüsünü belirten bir öznitelik uygulamak gerekir. Bir öznitelik, bir Özel UI türü Düzenleyici bir özellik ile ilişkilendirmek için de kullanabilirsiniz. UI türü Düzenleyici, özellik ya da veri türünü düzenlemek için bir kullanıcı arabirimi sağlar. Bir renk seçici, UI türü Düzenleyici örneğidir. Bu konunun sonunda öznitelikleri örnekleri verilir.  
  
    > [!NOTE]
    >  Bir tür dönüştürücüsü veya UI türü Düzenleyici, özel bir özellik için kullanılabilir değilse, bir bölümünde anlatıldığı gibi uygulayabileceğiniz [tasarım zamanı desteğini genişletmek](https://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2).  
  
 Aşağıdaki kod parçası adlı bir özel özellik tanımlar `EndColor` özel denetim için `FlashTrackBar`.  
  
```vb  
Public Class FlashTrackBar  
   Inherits Control  
   ...  
   ' Private data member that backs the EndColor property.  
   Private _endColor As Color = Color.LimeGreen  
  
   ' The Category attribute tells the designer to display  
   ' it in the Flash grouping.   
   ' The Description attribute provides a description of  
   ' the property.   
   <Category("Flash"), _  
   Description("The ending color of the bar.")>  _  
   Public Property EndColor() As Color  
      ' The public property EndColor accesses _endColor.  
      Get  
         Return _endColor  
      End Get  
      Set  
         _endColor = value  
         If Not (baseBackground Is Nothing) And showGradient Then  
            baseBackground.Dispose()  
            baseBackground = Nothing  
         End If  
         ' The Invalidate method calls the OnPaint method, which redraws    
         ' the control.  
         Invalidate()  
      End Set  
   End Property  
   ...  
End Class  
```  
  
```csharp  
public class FlashTrackBar : Control {  
   ...  
   // Private data member that backs the EndColor property.  
   private Color endColor = Color.LimeGreen;  
   // The Category attribute tells the designer to display  
   // it in the Flash grouping.   
   // The Description attribute provides a description of  
   // the property.   
   [  
   Category("Flash"),  
   Description("The ending color of the bar.")  
   ]  
   // The public property EndColor accesses endColor.  
   public Color EndColor {  
      get {  
         return endColor;  
      }  
      set {  
         endColor = value;  
         if (baseBackground != null && showGradient) {  
            baseBackground.Dispose();  
            baseBackground = null;  
         }  
         // The Invalidate method calls the OnPaint method, which redraws   
         // the control.  
         Invalidate();  
      }  
   }  
   ...  
}  
```  
  
 Aşağıdaki kod parçası bir tür dönüştürücüsü ve UI türü Düzenleyici özelliğiyle ilişkilendirir `Value`. Bu durumda `Value` tamsayı ve bir varsayılan tür dönüştürücüsü ancak <xref:System.ComponentModel.TypeConverterAttribute> özniteliği geçerli bir özel tür dönüştürücüsü (`FlashTrackBarValueConverter`) yüzde olarak görüntülemek tasarımcı sağlar. UI türü düzenleyici `FlashTrackBarValueEditor`, görsel olarak görüntülenecek yüzdesini sağlar. Bu örnek ayrıca, bir tür dönüştürücüsü veya Düzenleyicisi tarafından belirtilen gösterir <xref:System.ComponentModel.TypeConverterAttribute> veya <xref:System.ComponentModel.EditorAttribute> öznitelik varsayılan dönüştürücü geçersiz kılar.  
  
```vb  
<Category("Flash"), _  
TypeConverter(GetType(FlashTrackBarValueConverter)), _  
Editor(GetType(FlashTrackBarValueEditor), _  
GetType(UITypeEditor)), _  
Description("The current value of the track bar.  You can enter an actual value or a percentage.")>  _  
Public ReadOnly Property Value() As Integer  
...  
End Property  
```  
  
```csharp  
[  
Category("Flash"),   
TypeConverter(typeof(FlashTrackBarValueConverter)),  
Editor(typeof(FlashTrackBarValueEditor), typeof(UITypeEditor)),  
Description("The current value of the track bar.  You can enter an actual value or a percentage.")  
]  
public int Value {  
...  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Forms Denetimlerindeki Özellikler](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 [ShouldSerialize ile Varsayılan Değerleri Tanımlama ve Yöntemleri Sıfırlama](../../../../docs/framework/winforms/controls/defining-default-values-with-the-shouldserialize-and-reset-methods.md)  
 [Özellik Değişti Olayları](../../../../docs/framework/winforms/controls/property-changed-events.md)  
 [Windows Forms Denetimlerindeki Öznitelikler](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)
