---
title: XML Dosyasını İşleme (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments [Visual Basic], parsing [Visual Basic]
ms.assetid: 78a15cd0-7708-4e79-85d1-c154b7a14a8c
ms.openlocfilehash: 524a54443b8f2365252f11282ca29fc492bef351
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43398579"
---
# <a name="processing-the-xml-file-visual-basic"></a>XML Dosyasını İşleme (Visual Basic)
Derleyici, kodunuzda belgeleri oluşturmak için etiketli her yapı için bir kimlik dizesi oluşturur. (Kodunuzu etiketleme hakkında daha fazla bilgi için bkz: [XML açıklama etiketleri](../../../visual-basic/language-reference/xmldoc/index.md).) Kimlik dizesi yapısını benzersiz olarak tanımlar. XML dosyasını işleme programları, karşılık gelen belirlemek için kimlik dizesi kullanabilirsiniz [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] meta verileri/yansıma öğesi.  
  
 XML dosyası kodunuzu hiyerarşik bir gösterimini değil; Düz listeyle her öğe için oluşturulan bir kimliği var.  
  
 Kimlik dizeleri oluşturduğunda, derleyici aşağıdaki kurallar gözlemler:  
  
-   Hiçbir boşluk dizesinde yerleştirilir.  
  
-   Kimlik dizesi ilk bölümünü izleyen iki nokta ile tek bir karakter ile tanımlanmakta üye türünü tanımlar. Aşağıdaki üye türleri kullanılır.  
  
|Karakter|Açıklama|  
|---|---|  
|N|ad alanı<br /><br /> Belge açıklamaları için bir ad alanı ekleyemezsiniz, ancak bunları CREF başvuruları yapabileceğiniz desteklenen durumlarda.|  
|T|Tür: `Class`, `Module`, `Interface`, `Structure`, `Enum`, `Delegate`|  
|F|alan: `Dim`|  
|P|Özellik: `Property` (varsayılan özellikleri dahil)|  
|M|yöntemi: `Sub`, `Function`, `Declare`, `Operator`|  
|E|olay: `Event`|  
|!|Hata dizesi<br /><br /> Dizenin geri kalanı, hata hakkında bilgi sağlar. Visual Basic Derleyicisi, çözümlenemeyen bağlantılar için hata bilgisi oluşturur.|  
  
-   İkinci bölümü `String` tam nitelikli ad alanı kökünde başlangıç öğesi adıdır. Öğesi, kendi kapsayan türleri ve ad alanı adı noktalarla ayrılmış. Öğenin adını nokta içeriyorsa, sayı işaretiyle değiştirilir (#). Öğe adını doğrudan sayı işareti olduğunu kabul edilir. Örneğin, tam olarak nitelenmiş adını `String` Oluşturucusu olacak `System.String.#ctor`.  
  
-   Yöntemi için bağımsız değişken varsa özellikleri ve yöntemleri, parantez içindeki bağımsız değişken listesini takip eder. Hiçbir bağımsız değişken varsa, hiçbir parantez yok. Bağımsız değişkenlerin virgülle ayrılır. Her bağımsız değişkeni kodlama doğrudan nasıl içinde kodlanır izleyen bir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] imzası.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod nasıl kimliği için bir sınıf dizeleri gösterir ve üyelerini oluşturulur.  
  
 [!code-vb[VbVbcnXmlDocComments#10](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/processing-the-xml-file_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)  
 [Nasıl yapılır: XML Belgesi Oluşturma](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
