---
title: Sanal üyeler
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- overridable members
- virtual members
- members [.NET Framework], virtual
ms.assetid: 8ff4eb97-0364-43ec-8a02-934b5cd94d19
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b92b648e7886fb0214238e32eacae2870b470340
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47216428"
---
# <a name="virtual-members"></a>Sanal üyeler
Sanal üyeler, bu nedenle alt davranışını değiştirme geçersiz kılınabilir. Bunlar geri çağırmaları sağladıkları genişletilebilirlik açısından oldukça benzer, ancak bunlar yürütme performans ve bellek tüketimi açısından daha iyi. Ayrıca, sanal üyeleri özel bir tür var olan bir tür (özelleştirmesi) oluşturma gerektiren senaryolar daha doğal gönderebilirsiniz.  
  
 Sanal üyeler geri çağrıları ve olayları daha iyi gerçekleştirir, ancak sanal olmayan yöntemlerde daha iyi gerçekleştirmeyin.  
  
 Sanal üyeler dezavantajı, bir sanal üye davranışını yalnızca derleme zamanında değiştirilebilir ' dir. Bir geri çağırma davranışını çalışma zamanında değiştirilebilir.  
  
 Geri çağırmalar (ve belki birden çok geri çağırmaları) gibi sanal üyelerini tasarlamanıza, test ve nedeni herhangi bir sanal üye çağrısı beklenmeyen şekilde geçersiz kılınabilir ve rastgele kod yürütebilir korumak yüksek maliyetlidir. Ayrıca, çok daha fazla çaba tasarlama ve bunları belgeleme maliyeti daha yüksek olacak şekilde sanal üyelerinin sözleşmeyi açıkça tanımlamak için genellikle gereklidir.  
  
 **X DO NOT** üyeleri sanal sürece bunu yapmak için iyi bir nedeniniz yoksa ve tasarlamak, test ve sanal üyeleri koruma ile ilgili tüm maliyetler farkında olun.  
  
 Bunlara uyumluluk bozup olmadan yapılabilecek değişiklikler açısından daha az forgiving sanal üyeleridir. Genellikle çağrıları sanal üyelerine satır içine alınmış olmadığından Ayrıca, sanal olmayan üyeleri yavaştır.  
  
 **✓ CONSIDER** yalnızca kesinlikle gerekli nedir için genişletilebilirlik sınırlama.  
  
 **✓ DO** korumalı erişilebilirlik ortak erişilebilirlik sanal üyeleri için tercih eder. Genel üyeler genişletilebilirlik (gerekliyse) bir korumalı sanal üye çağırarak sağlamanız gerekir.  
  
 Genel bir sınıf üyesi işlevleri doğru ortaklık kümesi söz konusu sınıfın doğrudan müşterileri için sağlamanız gerekir. Sanal üyeler sınıflarında geçersiz kılınacak tasarlanmıştır ve korumalı erişilebilirlik nerede kullanılabilmesi için tüm sanal genişletilebilirlik noktaları kapsamını belirlemek için harika bir yoludur.  
  
 *Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)  
- [Genişletilebilirlik için Tasarlama](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
