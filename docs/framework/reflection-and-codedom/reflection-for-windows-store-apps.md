---
title: "Windows Mağazası Uygulamaları için .NET Framework'te Yansıma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- reflection, Windows Store apps
- .NET for Windows Store apps, TypeInfo class
ms.assetid: 0d07090c-9b47-4ecc-81d1-29d539603c9b
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 80429810a46438cdbf7cf2993e5f3b0779d300c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="reflection-in-the-net-framework-for-windows-store-apps"></a>Windows Mağazası Uygulamaları için .NET Framework'te Yansıma
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] başlayarak .NET Framework, [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamasında kullanılmak üzere bir yansıma türü ve üye kümesini içerir. Bu türleri ve üyeleri de tam .NET Framework olarak kullanılabilir olan [.NET için Windows mağazası uygulamaları](http://go.microsoft.com/fwlink/?LinkID=225700). Bu belge, bunlar ile .NET Framework 4 ve daha önceki sürümlerdeki karşılıkları arasındaki temel farkları açıklar.  
  
 Bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulaması oluşturuyorsanız, [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]'de bulunan yansıma türlerini ve üyeleri kullanmanız gerekir. Bu türler ve üyeler, gerekli olmasa da aynı zamanda masaüstü uygulamalarında kullanılmak üzere mevcuttur, bu nedenle her iki uygulama türü için de aynı kodu kullanabilirsiniz.  
  
## <a name="typeinfo-and-assembly-loading"></a>TypeInfo ve Derleme Yükleme  
 [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]'de, <xref:System.Reflection.TypeInfo> sınıfı .NET Framework 4 <xref:System.Type> sınıfının bazı işlevlerini içerir. Bir <xref:System.Type> nesnesi, tür tanımını kendisi temsil ederken bir <xref:System.Reflection.TypeInfo> nesnesi, tür tanımına bir başvuruyu temsil eder. Bu, başvurdukları derlemenin çalışma zamanı tarafından yüklenmesine gerek olmadan <xref:System.Type> nesnelerini işlemenizi sağlar. İlişkili <xref:System.Reflection.TypeInfo> nesnesini almak, derlemeyi yüklenmeye zorlar.  
  
 <xref:System.Reflection.TypeInfo>, <xref:System.Type>'da kullanılabilir olan üyelerin birçoğunu içerir ve [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]'deki yansıma özelliklerinin birçoğu <xref:System.Reflection.TypeInfo> nesnesinin koleksiyonlarını döndürür. Bir <xref:System.Reflection.TypeInfo> nesnesinden <xref:System.Type> nesnesini almak için <xref:System.Reflection.IReflectableType.GetTypeInfo%2A> yöntemini kullanın.  
  
## <a name="query-methods"></a>Sorgu yöntemleri  
 [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]'da, dizileri döndüren yöntemler yerine <xref:System.Collections.Generic.IEnumerable%601> öğesini döndüren yansıma özelliklerini kullanın. Yansıma bağlamları, büyük derlemeler veya türler için bu koleksiyonların yavaş çapraz geçişini uygulayabilir.  
  
 Yansıma özellikleri, özel bir nesne için, kalıtım ağacına dönmek yerince yalnızca belirtilen yöntemleri kullanırlar. Ayrıca, filtreleme için <xref:System.Reflection.BindingFlags> parametrelerini kullanmaz. Bunun yerine filtreleme işlemi, döndürülen koleksiyonlarda LINQ sorguları kullanılarak kullanıcı kodu içinde yer alır. Çalışma zamanıyla oluşan yansıma nesneleri için (örneğin, `typeof(Object)`'in sonucu olarak) devralma ağacının çapraz geçişi en iyi, <xref:System.Reflection.RuntimeReflectionExtensions> sınıfının yardımcı yöntemleri kullanılarak gerçekleştirilir. Özelleştirilmiş yansıma bağlamlarından gelen nesnelerin tüketicileri bu yöntemleri kullanamaz ve kendileri devralma ağacını kendileri geçirmeleri gerekir.  
  
## <a name="restrictions"></a>Kısıtlamalar  
 Bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamasında, bazı .NET Framework türlerine ve üyelerine erişim sınırlıdır. Örneğin, bir [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] nesnesini kullanarak, <xref:System.Reflection.MethodInfo>'a dahil edilmeyen .NET Framework yöntemlerini çağıramazsınız. Ayrıca, [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] ve <xref:System.Runtime.InteropServices.Marshal> üyeleri gibi, bir <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal> uygulamasının bağlamında güvenli olarak nitelendirilmeyen belirli tür ve üyeler engellenir. Bu kısıtlama yalnızca .NET Framework türlerini ve üyelerini etkiler; normalde yaptığınız gibi kodunuzu veya üçüncü taraf kodunu çağırabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Bu örnek, devralınan yöntemler ve özellikler dahil olmak üzere [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] türünün yöntemlerini ve özelliklerini almak için <xref:System.Globalization.Calendar> öğesinde yansıma türlerini ve üyelerini kullanır. Bu kodu çalıştırmak için için kod dosyası yapıştırın bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] içeren sayfasını bir [Windows.UI.Xaml.Controls.Textblock](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx) adlı Denetim `textblock1` yansıma adlı bir projede. Yalnızca bu kodu farklı bir ada sahip bir proje içinde yapıştırırsanız, projenizin eşleştirmek için ad alanı adı değiştirdiğinizden emin olun.  
  
 [!code-csharp[System.ReflectionWinStoreApp#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.reflectionwinstoreapp/cs/mainpage.xaml.cs#1)]
 [!code-vb[System.ReflectionWinStoreApp#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.reflectionwinstoreapp/vb/mainpage.xaml.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yansıma](../../../docs/framework/reflection-and-codedom/reflection.md)  
 [.NET için Windows mağazası uygulamaları – desteklenen API'leri](http://go.microsoft.com/fwlink/?LinkID=225700)