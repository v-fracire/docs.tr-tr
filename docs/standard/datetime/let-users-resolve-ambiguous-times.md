---
title: 'Nasıl yapılır: kullanıcıların belirsiz saatleri çözmelerine olanak tanır'
ms.date: 04/10/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: bca874ee-5b68-4654-8bbd-3711220ef332
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 91e80f44934092007f6f842f0694789d49321446
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863557"
---
# <a name="how-to-let-users-resolve-ambiguous-times"></a>Nasıl yapılır: kullanıcıların belirsiz saatleri çözmelerine olanak tanır

Belirsiz bir saat birden fazla Eşgüdümlü Evrensel Saat (UTC için) eşleyen bir zamandır. Saatin geri sürede gibi standart saati kendi saat diliminin gün ışığından yararlanma saatine geçiş sırasında ayarlanır oluşur. Belirsiz bir saat işlerken, aşağıdakilerden birini yapabilirsiniz:

* Bir öğenin kullanıcı tarafından girilen veriler belirsiz saat ise belirsizliği çözmek için kullanıcıya bırakabilirsiniz.

* Saat UTC'ye nasıl eşlendiğini hakkında bir olduğu varsayımını yaparsınız. Örneğin, belirsiz bir süre içinde saat diliminin standart saat her zaman gösterilir varsayabilirsiniz.

Bu konuda, bir kullanıcının belirsiz bir saat çözmek olanak gösterilmektedir.

### <a name="to-let-a-user-resolve-an-ambiguous-time"></a>Belirsiz bir saat çözmek kullanıcı izin vermek için

1. Tarih ve saat tarafından kullanıcı girişi alın.

2. Çağrı <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> zaman belirsiz olup olmadığını belirlemek için yöntemi.

3. Zaman belirsiz ise, çağrı <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> dizisini almak için yöntemi <xref:System.TimeSpan> nesneleri. Belirsiz saat eşleyebilirsiniz bir UTC farkı dizideki her öğe içerir.

4. Kullanıcı Seç istenen uzaklığı olanak tanır.

5. UTC tarihi ve saati yerel saate kullanıcı tarafından seçilen uzaklığı çıkararak alın.

6. Çağrı `static` (`Shared` Visual Basic. NET'te) <xref:System.DateTime.SpecifyKind%2A> UTC tarih ve saat değerinin ayarlanacak yöntemi <xref:System.DateTime.Kind%2A> özelliğini <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.

## <a name="example"></a>Örnek

Aşağıdaki örnek bir tarih ve saat girmesini ister ve belirsiz ise belirsiz saat eşlendiği UTC saati seçmesine izin verir.

[!code-csharp[System.TimeZone2.Concepts#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#11)]
[!code-vb[System.TimeZone2.Concepts#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#11)]

Örnek kod setinin bir dizi kullanan <xref:System.TimeSpan> belirsiz saat UTC olası uzaklıklarını belirtmek için nesnelerdeki. Ancak, bu uzaklıkları kullanıcıya anlamlı olması pek olası değildir. Uzaklık anlamını açıklamak için bir uzaklık yerel saat diliminin standart saat veya kendi yaz saati temsil edip etmediğini kod da notlar. Kodu, hangi zaman standart belirler ve hangi zaman Yaz uzaklık değeri ile karşılaştırarak <xref:System.TimeZoneInfo.BaseUtcOffset%2A> özelliği. Bu özellik, saat diliminin Standart Saati ile UTC arasındaki farkı gösterir.

Bu örnekte, yerel saat dilimi için tüm başvuruları aracılığıyla yapılan <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> özelliği; yerel saati dilimi hiçbir zaman bir nesne değişkenine atanır. Bunun nedeni önerilen uygulama, bir çağrı <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> metodu geçersiz kılar, yerel saat dilimi atandığı herhangi bir nesne.

## <a name="compiling-the-code"></a>Kod derleme

Bu örnek gerektirir:

* Projeye System.Core.dll öğesine başvuru eklenmesi gerektiğini.

* Olduğunu <xref:System> ad alanı içeri aktarılacak `using` deyimi (C# kodunda gereklidir).

## <a name="see-also"></a>Ayrıca bkz.

* [Tarihler, saatler ve saat dilimleri](../../../docs/standard/datetime/index.md)
* [Nasıl yapılır: Belirsiz saatleri çözme](../../../docs/standard/datetime/resolve-ambiguous-times.md)
