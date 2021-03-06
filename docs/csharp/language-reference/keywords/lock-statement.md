---
title: lock deyimi (C# Başvurusu)
description: C# lock deyiminin paylaşılan kaynak iş parçacığı erişimi eşitlemek için kullanın
ms.date: 08/28/2018
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
ms.openlocfilehash: 2b6fbfb2f81d7745c4effb9ea0087f34cc872a6c
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43858362"
---
# <a name="lock-statement-c-reference"></a>lock deyimi (C# Başvurusu)

`lock` Deyimi belirli bir nesne için karşılıklı dışlama kilidini alır, bir deyim bloğunu yürütür ve ardından kilidi serbest bırakır. Kilidi açık tutulduğu sürece kilidi tutan iş parçacığı yeniden alabilir ve kilidi serbest bırakır. Başka bir iş parçacığı kilidi elde edilen engellenir ve kilidi serbest bırakılıncaya kadar bekler.

`lock` Deyimdir biçimi

```csharp
lock (x)
{
    // Your code...
}
```

Burada `x` bir ifade olan bir [başvuru türüne](reference-types.md). Tam olarak eşdeğerdir

```csharp
object __lockObj = x;
bool __lockWasTaken = false;
try
{
    System.Threading.Monitor.Enter(__lockObj, ref __lockWasTaken);
    // Your code...
}
finally
{
    if (__lockWasTaken) System.Threading.Monitor.Exit(__lockObj);
}
```

Kod kullandığından bir [try... finally](try-finally.md) bloğu kilidi serbest gövdesi içinde bir özel durum olsa bile bir `lock` deyimi.

Kullanamazsınız [await](await.md) gövdesinde anahtar sözcüğü bir `lock` deyimi.

## <a name="remarks"></a>Açıklamalar

İş parçacığı paylaşılan kaynağa erişimi eşitlediğinizde, adanmış Pro instanci objektu kilitleme (örneğin, `private readonly object balanceLock = new object();`) ya da bir kilit nesnesi olarak kodun ilgisiz parçaları tarafından kullanılmak üzere düşüktür, başka bir örneği. Kilitlenme veya kilit Çekişme neden olabilir, farklı paylaşılan kaynaklar için aynı kilit nesne örneğini kullanarak kaçının. Özellikle, kullanmaktan kaçının.

- `this` (arayanlar tarafından bir kilit olarak kullanılabilir),
- <xref:System.Type> örnekler (tarafından alınabilir [typeof](typeof.md) işleci veya yansıma),
- dize değişmez değerleri dahil olmak üzere, dize örnekleri,

nesneleri kilitle.

## <a name="example"></a>Örnek

Aşağıdaki örnekte tanımlayan bir `Account` özel erişimi eşitler sınıfı `balance` üzerinde adanmış bir kilitleme alanı `balanceLock` örneği. Kilitleme sağlar için aynı örneği kullanarak `balance` alanı güncelleştirilemiyor aynı anda arama girişimi iki iş parçacığı tarafından `Debit` veya `Credit` yöntemleri aynı anda.

[!code-csharp[lock-statement-example](~/samples/snippets/csharp/keywords/LockStatementExample.cs)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.SpinLock?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [C# başvurusu](../index.md)
- [C# Anahtar Sözcükleri](index.md)
- [Deyim Anahtar Sözcükleri](statement-keywords.md)
- [Birbirine kenetlenmiş işlemler](../../../standard/threading/interlocked-operations.md)
- [Eşitleme temellerine genel bakış](../../../standard/threading/overview-of-synchronization-primitives.md)