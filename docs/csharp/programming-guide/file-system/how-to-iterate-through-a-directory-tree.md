---
title: 'Nasıl yapılır: Dizin Ağacı ile Yineleme (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- iterating through folders [C#]
- file iteration [C#]
ms.assetid: c4be4a75-6b1b-46a7-9d38-bab353091ed7
ms.openlocfilehash: 1aac40793fabe152e18a1bf1b634058e85b31481
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43515767"
---
# <a name="how-to-iterate-through-a-directory-tree-c-programming-guide"></a>Nasıl yapılır: Dizin Ağacı ile Yineleme (C# Programlama Kılavuzu)
Her iç içe geçmiş alt dizinde bir belirtilen kök klasöre herhangi derinliği her dosyaya erişmek deyimi "dizin ağacı yineleme" anlamına gelir. Mutlaka her dosyayı açmak gerekmez. Yalnızca dosya veya alt dizini olarak adını alabilirsiniz bir `string`, veya biçiminde ek bilgi almak bir <xref:System.IO.FileInfo?displayProperty=nameWithType> veya <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> nesne.  
  
> [!NOTE]
>  Windows koşulları "dizin" ve "klasörü" birbirinin yerine kullanılır. Çoğu belgelerini ve kullanıcı arabirimi metinlerini "klasörü" terimini kullanır ancak [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] class kitaplığını kullanan "directory" terimi  
  
 En basit örnekte, bildiğiniz belirli bir belirtilen kökü altındaki tüm dizinleri erişim izinlerine sahip olduğunuz kullanabileceğiniz `System.IO.SearchOption.AllDirectories` bayrağı. Bu bayrak, belirtilen desenle eşleşen tüm iç içe geçmiş alt döndürür. Aşağıdaki örnek, bu bayrak kullanma işlemini gösterir.  
  
```csharp  
root.GetDirectories("*.*", System.IO.SearchOption.AllDirectories);  
```  
  
 Belirtilen kök dizinler herhangi biri neden olursa olan zayıflık Bu yaklaşımda bir <xref:System.IO.DirectoryNotFoundException> veya <xref:System.UnauthorizedAccessException>, tüm yöntem başarısız ve yok dizinleri döndürür. Kullandığınızda, aynı durum geçerlidir <xref:System.IO.DirectoryInfo.GetFiles%2A> yöntemi. Belirli klasörlerde bu özel durumları işlemek varsa, dizin ağacında aşağıdaki örneklerde gösterildiği gibi el ile gezin gerekir.  
  
 Dizin ağacı el ile gezin, alt dizinleri ilk işleyebilir (*öncesi sırası geçişi*), veya dosyaları ilk (*sonrası sırası geçişi*). Öncesi sırası geçişi gerçekleştirirseniz, ağacın tamamı geçerli klasör altında doğrudan bu klasörde kendisini dosyaları ile Yinelem önce yol. Bu belgenin ilerleyen bölümlerinde verilen örneklerde sonrası sırası geçişi gerçekleştirmek, ancak bunları öncesi sırası geçişi gerçekleştirmek için kolayca değiştirebilirsiniz.  
  
 Başka bir yineleme veya bir yığın tabanlı geçişi kullanıp kullanmayacağınızı seçenektir. Bu belgenin ilerleyen bölümlerinde verilen örneklerde iki yaklaşımı gösterir.  
  
 Çeşitli dosyalar ve klasörler üzerindeki işlemleri gerçekleştirmek varsa, bu örnekleri yeniden düzenleme işlemi, tek bir temsilci aracılığıyla çağırabilirsiniz ayrı işlevler halinde tarafından modülerleştirmek.  
  
> [!NOTE]
>  NTFS dosya sistemleri içerebilir *yeniden ayrıştırma noktaları* biçiminde *birleşim noktaları*, *simgesel bağlantılar*, ve *sabit bağlantılar*. .NET Framework yöntemlerini gibi <xref:System.IO.DirectoryInfo.GetFiles%2A> ve <xref:System.IO.DirectoryInfo.GetDirectories%2A> yeniden ayrıştırma noktası altında herhangi bir alt dizini döndürmez. Bu davranış, iki yeniden ayrıştırma noktası, birbirlerine başvurduğunuzda sonsuz döngüye girme riskini karşı korur. Genel olarak, yanlışlıkla değil değiştirdiğinizde ya da dosyaları silin, emin olmak için yeniden ayrıştırma noktaları ile dağıttığınızda, son derece dikkatli olun kullanmanız gerekir. Yeniden ayrıştırma noktaları üzerinde kesin denetim gerekiyorsa, platform çağırma kullanma veya uygun Win32 dosya sistemi yöntemleri doğrudan çağırmak için yerel kod.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl bir dizin ağacında özyineleme kullanarak size yol gösterir. Özyinelemeli yaklaşım şık, ancak dizin ağacında büyük ve iç içe ise bir yığın taşması özel durumuna neden olabilir.  
  
 İşlenen belirli özel durumları ve her bir dosya veya klasör üzerinde gerçekleştirilen belirli eylemler yalnızca örnek olarak verilmiştir. Belirli gereksinimlerinizi karşılamak için bu kodu değiştirmeniz gerekir. Daha fazla bilgi için koddaki açıklamalara bakın.  
  
 [!code-csharp[csFilesandFolders#1](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-iterate-through-a-directory-tree_1.cs)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, özyineleme kullanmadan dosya ve klasörleri dizin ağacı ile yineleme gösterilmektedir. Bu tekniği kullanan genel <xref:System.Collections.Generic.Stack%601> son giren ilk çıkar (LIFO) yığında olan koleksiyon türü.  
  
 İşlenen belirli özel durumları ve her bir dosya veya klasör üzerinde gerçekleştirilen belirli eylemler yalnızca örnek olarak verilmiştir. Belirli gereksinimlerinizi karşılamak için bu kodu değiştirmeniz gerekir. Daha fazla bilgi için koddaki açıklamalara bakın.  
  
 [!code-csharp[csFilesandFolders#2](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-iterate-through-a-directory-tree_2.cs)]  
  
 Genel olarak, uygulamanızı açmak için izni olup olmadığını belirlemek için her klasör test çok zaman alır. Bu nedenle, kod örneği bu işlemde bölümü yalnızca kapsayan bir `try/catch` blok. Değiştirebileceğiniz `catch` izinlerinizi yükseltmek ve yeniden erişmek deneyin bir klasöre erişimi reddedildiğinde, böylece engelleyin. Bir kural olarak, yalnızca bilinmeyen bir durumda, uygulamanızın çıkmadan işleyebileceği özel durumları yakalayın.  
  
 Bir dizin ağacında içeriğini bellekte veya diskte depolamanız gerekir, yalnızca depolamak için en iyi seçenek olduğu <xref:System.IO.FileSystemInfo.FullName%2A> özelliği (tür `string`) her dosya için. Bu dize daha sonra yeni bir kullanabilirsiniz <xref:System.IO.FileInfo> veya <xref:System.IO.DirectoryInfo> nesne gerektiğinde veya ek işlem gerektiren her türlü dosyayı açmak.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Sağlam bir dosya yineleme kod dosya sistemi birçok karmaşıklığını dikkate almanız gerekir. Windows dosya sistemi hakkında daha fazla bilgi için bkz. [NTFS teknik başvuru](https://technet.microsoft.com/library/81cc8a8a-bd32-4786-a849-03245d68d8e4).  
  
## <a name="see-also"></a>Ayrıca Bkz.

- <xref:System.IO>  
- [LINQ ve Dosya Dizinleri](../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)  
- [Dosya sistemi ve kayıt defteri (C# programlama Kılavuzu)](../../../csharp/programming-guide/file-system/index.md)
