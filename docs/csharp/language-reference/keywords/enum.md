---
title: enum anahtar sözcüğü (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- enum
- enum_CSharpKeyword
helpviewer_keywords:
- enum keyword [C#]
ms.assetid: bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c
ms.openlocfilehash: a64559ac1127f5ec296cf3892dd521c3ad8ac2be
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44086156"
---
# <a name="enum-c-reference"></a>enum (C# Başvurusu)

`enum` Anahtar sözcüğü bir numaralandırma, numaralandırıcı listesi olarak adlandırılan sabitler kümesinden oluşan ayrı bir türü bildirmek için kullanılır.  

Genellikle ad alanındaki tüm sınıflar ile eşit kolaylık erişebilmeleri doğrudan bir ad alanındaki bir numaralandırma tanımlamak idealdir. Ancak, bir sabit listesi bir sınıf veya yapı içinde yuvalanabilir.

Varsayılan olarak, ilk Numaralandırıcı değeri 0 olan ve art arda gelen her Numaralandırıcı değeri 1 artar. Örneğin, aşağıdaki sabit listesi içinde `Sat` olduğu `0`, `Sun` olduğu `1`, `Mon` olduğu `2`vb.

```csharp
enum Day {Sat, Sun, Mon, Tue, Wed, Thu, Fri};
```

Numaralandırıcılar başlatıcılar varsayılan değerlerini geçersiz kılması için aşağıdaki örnekte gösterildiği gibi kullanabilirsiniz.

```csharp
enum Day {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};
```

Bu sabit listesi öğeleri dizisi başlangıç zorlanır `1` yerine `0`. Ancak, 0 değerine sahip bir sabit dahil olmak üzere önerilir. Daha fazla bilgi için [Numaralandırma türleri](../../programming-guide/enumeration-types.md).

Her sabit listesi türünde herhangi bir Entegral türü olabilir bir temel türü dışında [char](char.md). Sabit listesi öğeleri listesinin temel alınan türü varsayılandır [int](int.md). Bir numaralandırma başka bir integral türü gibi bildirmek için [bayt](byte.md), aşağıdaki örnekte gösterildiği gibi türü tarafından izlenen tanımlayıcısı sonra bir virgül kullanın.

```csharp
enum Day : byte {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};
```

Enum için onaylanan türler [bayt](byte.md), [sbyte](sbyte.md), [kısa](short.md), [ushort](ushort.md), [int](int.md), [uint](uint.md), [uzun](long.md), veya [ulong](ulong.md).

Türünde bir değişken `Day` temel alınan türü; aralığında herhangi bir değer atanabilir değer için adlandırılmış sabitler sınırlı değildir.

Varsayılan değer olan bir `enum E` ifade tarafından üretilen değer `(E)0`.

> [!NOTE]
> Bir numaralandırıcı adı boşluk içeremez.

Her Numaralandırıcı için ne kadar depolama alanı ayrılır, temel alınan türünü belirtir. Ancak, bir açık tür dönüştürme dönüştürmek gerekli `enum` türü için bir tamsayı türü. Örneğin aşağıdaki deyim, numaralandırıcı atar `Sun` türünde bir değişkene [int](int.md) dönüştürmek için bir tür dönüştürme kullanılarak `enum` için `int`.

```csharp
int x = (int)Day.Sun;
```

Uyguladığınızda <xref:System.FlagsAttribute?displayProperty=nameWithType> bit ile birleştirilebilir öğeleri içeren bir sabit listesi `OR` işlemi, öznitelik davranışını etkileyen `enum` bazı araçlarla kullanıldığında. Gibi araçları kullanın, bu değişiklikler fark <xref:System.Console> sınıfı yöntemleri ve ifade değerlendiricisi. (Üçüncü örneğe bakın.)

## <a name="robust-programming"></a>Güçlü programlama

Tek tek bir sabit listesi değerlerinin tüm başvurular olduğu herhangi bir sabit olduğu gibi sayısal değişmez değerleri için derleme zamanında dönüştürülür. Bu sürüm ile ilgili olası sorunları açıklandığı gibi oluşturabilirsiniz [sabitleri](../../programming-guide/classes-and-structs/constants.md).

Sabit listeleri yeni sürümleri için ek değerler atama veya yeni bir sürümünde, sabit listesi üyelerinin değerlerini değiştirmek için bağımlı kaynak kodunuz için sorunlara neden olabilir. Sabit listesi değerlerinin sık sık kullanılır [geçiş](switch.md) deyimleri. Ek öğeler için eklenip eklenmediğini `enum` varsayılan bölümün switch ifadesinin türü beklenmedik bir şekilde seçilebilir.

Diğer geliştiricilerin kodunuzu kullanırsanız, yeni öğeler için eklenirse kodlarını nasıl yanıt vermesini hakkında yönergeleri sağlamalıdır `enum` türleri.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, bir numaralandırma `Day`, bildirilir. İki numaralandırıcılar açıkça tamsayıya dönüştürülüp ve tamsayı değişkenine atanır.

[!code-csharp[csrefKeywordsTypes#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#10)]

## <a name="example"></a>Örnek

Aşağıdaki örnekte, temel türünde seçenek bildirmek için kullanılan bir `enum` üyeleri, tür `long`. Sabit listesi türünü temel olsa bile dikkat `long`, numaralandırma üyelerini hala açıkça türüne dönüştürülmesi gerekir `long` kullanarak bir cast.

[!code-csharp[csrefKeywordsTypes#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#11)]

## <a name="example"></a>Örnek

Aşağıdaki kod örneği kullanım ve etkisini gösterir <xref:System.FlagsAttribute?displayProperty=nameWithType> özniteliği bir `enum` bildirimi.

[!code-csharp[csrefKeywordsTypes#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#12)]

## <a name="comments"></a>Açıklamalar

Kaldırırsanız `Flags`, örnek aşağıdaki değerleri görüntüler:

`5`

`5`

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)  
- [Sabit Listesi Türleri](../../programming-guide/enumeration-types.md)  
- [C# Anahtar Sözcükleri](index.md)  
- [Tam Sayı Türleri Tablosu](integral-types-table.md)  
- [Yerleşik Türler Tablosu](built-in-types-table.md)  
- [Örtük Sayısal Dönüştürmeler Tablosu](implicit-numeric-conversions-table.md)  
- [Açık Sayısal Dönüştürmeler Tablosu](explicit-numeric-conversions-table.md)  
- [Enum adlandırma kuralları](../../../standard/design-guidelines/names-of-classes-structs-and-interfaces.md#naming-enumerations)
