---
title: Öğe, öznitelik ve düğümleri bir XML Tree3 değiştirme
ms.date: 07/20/2015
ms.assetid: 0ed22e4e-4c6b-4eb1-b0eb-06685efd8c33
ms.openlocfilehash: 9567d0c6c5cd4853eeb2a86066cd1a805f20a031
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43777356"
---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a>Öğe, öznitelik ve düğümleri bir XML ağacı değiştirme
Bir öğe, alt öğelerini ve özniteliklerini değiştirmek için kullanabileceğiniz özellikler ve yöntemler aşağıdaki tabloda özetlenmiştir.  
  
 Aşağıdaki yöntemlerden değiştirme bir <xref:System.Xml.Linq.XElement>.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>|Bir öğe ayrıştırılmış XML ile değiştirir.|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|Bir öğenin tüm içeriğin (alt düğümleri ve öznitelikleri) kaldırır.|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|Bir öğenin öznitelikleri kaldırır.|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=nameWithType>|Bir öğenin tüm içeriğin (alt düğümleri ve öznitelikleri) değiştirir.|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=nameWithType>|Bir öğenin öznitelikleri değiştirir.|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|Bir özniteliğin değerini ayarlar. Öznitelik yoksa oluşturur. Değer ayarlanmışsa `null`, öznitelik kaldırır.|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|Bir alt öğenin değerini ayarlar. Öğe yoksa oluşturur. Değer ayarlanmışsa `null`, öğeyi kaldırır.|  
|<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>|Bir öğenin içeriğini (alt düğümleri) belirtilen metinle değiştirir.|  
|<xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=nameWithType>|Bir öğenin değerini ayarlar.|  
  
 Aşağıdaki yöntemlerden değiştirme bir <xref:System.Xml.Linq.XAttribute>.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>|Bir özniteliğin değerini ayarlar.|  
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=nameWithType>|Bir özniteliğin değerini ayarlar.|  
  
 Aşağıdaki yöntemlerden değiştirme bir <xref:System.Xml.Linq.XNode> (dahil olmak üzere bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument>).  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=nameWithType>|Bir düğüm, yeni içerikle değiştirir.|  
  
 Aşağıdaki yöntemlerden değiştirme bir <xref:System.Xml.Linq.XContainer> (bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument>).  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=nameWithType>|Alt düğüm, yeni içerikle değiştirir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [(LINQ to XML) XML ağaçlarını değiştirme (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
