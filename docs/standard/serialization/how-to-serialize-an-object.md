---
title: 'Nasıl yapılır: bir nesneyi serileştirmek'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
ms.assetid: a1207d05-32b2-4953-8582-959607991227
ms.openlocfilehash: e4d6e3edb15dbf5ba4b7ec7f8658fec1a618d315
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45748581"
---
# <a name="how-to-serialize-an-object"></a>Nasıl yapılır: bir nesneyi serileştirmek
Bir nesneyi serileştirmek için önce sıralanabilir ve ortak özelliklerini ve alanları ayarlamak için olan nesne oluşturun. Bunu yapmak için XML akışı, bir akış olarak veya bir dosya olarak depolanır taşıma biçimi belirlemeniz gerekir. XML Akışı kalıcı bir biçimde kaydedilmesi gerekir, örneğin, oluşturun bir <xref:System.IO.FileStream> nesne.  
  
> [!NOTE]
>  Daha fazla XML serileştirme örnekler için bkz. [XML serileştirme örnekler](../../../docs/standard/serialization/examples-of-xml-serialization.md).  
  
### <a name="to-serialize-an-object"></a>Bir nesneyi serileştirmek için  
  
1.  Nesne oluşturun ve kendi ortak alanları ve özelliklerini ayarlayın.  
  
2.  Oluşturmak bir <xref:System.Xml.Serialization.XmlSerializer> kullanarak nesnenin türü. Daha fazla bilgi için <xref:System.Xml.Serialization.XmlSerializer> sınıf oluşturucu.  
  
3.  Çağrı <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> bir XML akışı veya nesnenin ortak özellikler ve alanları dosya gösterimini oluşturmak için yöntemi. Aşağıdaki örnek, bir dosya oluşturur.  
  
    ```vb  
    Dim myObject As MySerializableClass = New MySerializableClass()  
    ' Insert code to set properties and fields of the object.  
    Dim mySerializer As XmlSerializer = New XmlSerializer(GetType(MySerializableClass))  
    ' To write to a file, create a StreamWriter object.  
    Dim myWriter As StreamWriter = New StreamWriter("myFileName.xml")  
    mySerializer.Serialize(myWriter, myObject)  
    myWriter.Close()  
    ```  
  
    ```csharp  
    MySerializableClass myObject = new MySerializableClass();  
    // Insert code to set properties and fields of the object.  
    XmlSerializer mySerializer = new   
    XmlSerializer(typeof(MySerializableClass));  
    // To write to a file, create a StreamWriter object.  
    StreamWriter myWriter = new StreamWriter("myFileName.xml");  
    mySerializer.Serialize(myWriter, myObject);  
    myWriter.Close();  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Serileştirmeye Giriş](../../../docs/standard/serialization/introducing-xml-serialization.md)  
- [Nasıl yapılır: Nesneyi Seri Durumdan Çıkarma](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
