---
title: 'Nasıl yapılır: .NET Framework Yönergeleriyle Uyumlu Olayları Yayımlama (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], implementation guidelines
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
ms.openlocfilehash: 9a17aaec20b03325abadfcc168f7ac4653f300df
ms.sourcegitcommit: daa8788af67ac2d1cecd24f9f3409babb2f978c9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47862165"
---
# <a name="how-to-publish-events-that-conform-to-net-framework-guidelines-c-programming-guide"></a>Nasıl yapılır: .NET Framework Yönergeleriyle Uyumlu Olayları Yayımlama (C# Programlama Kılavuzu)
Aşağıdaki yordam standarda olayları ekleme göstermektedir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sınıflar ve yapılar için desen. Tüm olaylar [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sınıf kitaplığı temel <xref:System.EventHandler> temsilci, olduğu gibi tanımlanır:  
  
```csharp  
public delegate void EventHandler(object sender, EventArgs e);  
```  
  
> [!NOTE]
>  [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)] Bu temsilcinin genel bir sürümünde <xref:System.EventHandler%601>. Aşağıdaki örnekler, iki sürümünü kullanmayı gösterir.  
  
 Tüm geçerli temsilci türünde, bir değer döndürmesi bile temsilciler tanımladığınız sınıflarda olayları temel alabilir ancak genellikle olaylarınızı için temel önerilir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] deseni kullanılarak <xref:System.EventHandler>aşağıdaki örnekte gösterildiği gibi.  
  
### <a name="to-publish-events-based-on-the-eventhandler-pattern"></a>EventHandler deseni temel alınarak olayları yayımlamak için  
  
1.  (Adım 3a özel verilerle olayınızı göndermek yoksa gidin ve bu adımı atlayın.) Bir kapsamda yayımcısı ve abonesi sınıfların görebildiği özel verileriniz için sınıf bildirme. Ardından, özel olay verisini tutmak için gerekli üyeleri ekleyin. Bu örnekte, basit bir dize döndürülür.  
  
    ```csharp  
    public class CustomEventArgs : EventArgs  
    {  
        public CustomEventArgs(string s)  
        {  
            msg = s;  
        }  
        private string msg;  
        public string Message  
        {  
            get { return msg; }  
        }   
    }  
    ```  
  
2.  (Genel sürümünü kullanıyorsanız bu adımı atlayın <xref:System.EventHandler%601> .) Yayımlama sınıfınızın bir Temsilcide bildirin. İle biten bir ad verin *EventHandler*. İkinci parametresi, özel, EventArgs türünü belirtir.  
  
    ```csharp  
    public delegate void CustomEventHandler(object sender, CustomEventArgs a);  
    ```  
  
3.  Olay yayımlama sınıfınızda, aşağıdaki adımlardan birini kullanarak bildirin.  
  
    1.  Özel bir EventArgs sınıf varsa, genel olmayan EventHandler temsilci olay türünüz olacaktır. Zaten içinde bildirildiği için temsilci bildirmenize gerek olmayan <xref:System> C# projesi oluşturduğunuzda, dahil edilen ad alanı. Yayımcı sınıfa aşağıdaki kodu ekleyin.  
  
        ```csharp  
        public event EventHandler RaiseCustomEvent;  
        ```  
  
    2.  Genel olmayan sürümünü kullanıyorsanız <xref:System.EventHandler> ve türetilen özel bir sınıf sahip <xref:System.EventArgs>, yayımlama, sınıf içinde olay bildirmek ve 2. adımda, bir temsilci türü olarak kullanın.  
  
        ```csharp  
        public event CustomEventHandler RaiseCustomEvent;  
        ```  
  
    3.  Genel sürüm kullanıyorsanız, özel bir temsilci ihtiyacınız yoktur. Bunun yerine, yayımlama sınıfınızda, olay türü olarak belirttiğiniz `EventHandler<CustomEventArgs>`, açılı ayraçlar arasında kendi sınıfının adı değiştirme.  
  
        ```csharp  
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;  
        ```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, özel bir EventArgs sınıfını kullanarak önceki adımları göstermektedir ve <xref:System.EventHandler%601> olay türü.  
  
 [!code-csharp[csProgGuideEvents#2](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-publish-events-that-conform-to-net-framework-guidelines_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- <xref:System.Delegate>  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Olaylar](../../../csharp/programming-guide/events/index.md)  
- [Temsilciler](../../../csharp/programming-guide/delegates/index.md)
