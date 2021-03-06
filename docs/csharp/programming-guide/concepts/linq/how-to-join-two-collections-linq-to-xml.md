---
title: 'Nasıl yapılır: iki koleksiyonu (LINQ to XML) birleştirme (C#)'
ms.date: 07/20/2015
ms.assetid: 7b817ede-911a-4cff-9dd3-639c3fc228c9
ms.openlocfilehash: 00db2decfb8595c32e86f76c8aa139d91e75d112
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43513536"
---
# <a name="how-to-join-two-collections-linq-to-xml-c"></a>Nasıl yapılır: iki koleksiyonu (LINQ to XML) birleştirme (C#)
Bazen bir öğe veya öznitelik XML belgesindeki başka bir öğe veya öznitelik başvurabilir. Örneğin, [örnek XML dosyası: müşteriler ve siparişler (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md) XML belgesi, müşterilerin listesini ve siparişlerinin listesi içerir. Her `Customer` öğesi içeren bir `CustomerID` özniteliği. Her `Order` öğesi içeren bir `CustomerID` öğesi. `CustomerID` Öğesi her sırada başvurduğu `CustomerID` öznitelik bir müşteri.  
  
 Konu [örnek XSD dosyası: müşteriler ve siparişler](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md) bu belgeyi doğrulamak için kullanılan bir XSD içerir. Kullandığı `xs:key` ve `xs:keyref` , kurmak için XSD özelliklerinin `CustomerID` özniteliği `Customer` öğesi olan bir anahtar ve arasında ilişki kurmak için `CustomerID` her öğe `Order` öğesi ve `CustomerID` her öznitelik `Customer` öğesi.  
  
 İle [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], bu ilişkinin kullanarak yararlanabilirsiniz `join` yan tümcesi.  
  
 Kullanılabilir hiçbir dizin olduğundan birleştirme gibi zayıf çalışma zamanı performansını olacağını unutmayın.  
  
 Hakkında ayrıntılı bilgi için `join`, bkz: [birleştirme işlemleri (C#)](../../../../csharp/programming-guide/concepts/linq/join-operations.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek birleştirmeleri `Customer` öğelerine `Order` öğeleri içeren yeni bir XML belgesi oluşturur `CompanyName` siparişlerin öğesi.  
  
 Örnek Belge şemada uygun doğrular sorguyu çalıştırmadan önce [örnek XSD dosyası: müşteriler ve siparişler](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md). Bu, JOIN yan tümcesi her zaman çalışmasını sağlar.  
  
 Bu sorgu tüm ilk alır `Customer` öğeleri ve bunları birleştirir `Order` öğeleri. Yalnızca müşterilerle siparişler seçen bir `CustomerID` "K" büyüktür. Ardından yeni bir proje `Order` her sipariş içindeki müşteri bilgileri içeren öğe.  
  
 Bu örnekte aşağıdaki XML belgesi: [örnek XML dosyası: müşteriler ve siparişler (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).  
  
 Bu örnekte aşağıdaki XSD şeması: [örnek XSD dosyası: müşteriler ve siparişler](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md).  
  
 Bu şekilde katılma çok iyi gerçekleştirmez olduğunu unutmayın. Birleşimler, doğrusal bir arama yoluyla gerçekleştirilir. Karma tabloları veya performansa yardımcı olmak için dizinleri yoktur.  
  
```csharp  
XmlSchemaSet schemas = new XmlSchemaSet();  
schemas.Add("", "CustomersOrders.xsd");  
  
Console.Write("Attempting to validate, ");  
XDocument custOrdDoc = XDocument.Load("CustomersOrders.xml");  
  
bool errors = false;  
custOrdDoc.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("custOrdDoc {0}", errors ? "did not validate" : "validated");  
  
if (!errors)  
{  
    // Join customers and orders, and create a new XML document with  
    // a different shape.  
  
    // The new document contains orders only for customers with a  
    // CustomerID > 'K'  
    XElement custOrd = custOrdDoc.Element("Root");  
    XElement newCustOrd = new XElement("Root",  
        from c in custOrd.Element("Customers").Elements("Customer")  
        join o in custOrd.Element("Orders").Elements("Order")  
                   on (string)c.Attribute("CustomerID") equals  
                      (string)o.Element("CustomerID")  
        where ((string)c.Attribute("CustomerID")).CompareTo("K") > 0  
        select new XElement("Order",  
            new XElement("CustomerID", (string)c.Attribute("CustomerID")),  
            new XElement("CompanyName", (string)c.Element("CompanyName")),  
            new XElement("ContactName", (string)c.Element("ContactName")),  
            new XElement("EmployeeID", (string)o.Element("EmployeeID")),  
            new XElement("OrderDate", (DateTime)o.Element("OrderDate"))  
        )  
    );  
    Console.WriteLine(newCustOrd);  
}  
```  
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```  
Attempting to validate, custOrdDoc validated  
<Root>  
  <Order>  
    <CustomerID>LAZYK</CustomerID>  
    <CompanyName>Lazy K Kountry Store</CompanyName>  
    <ContactName>John Steel</ContactName>  
    <EmployeeID>1</EmployeeID>  
    <OrderDate>1997-03-21T00:00:00</OrderDate>  
  </Order>  
  <Order>  
    <CustomerID>LAZYK</CustomerID>  
    <CompanyName>Lazy K Kountry Store</CompanyName>  
    <ContactName>John Steel</ContactName>  
    <EmployeeID>8</EmployeeID>  
    <OrderDate>1997-05-22T00:00:00</OrderDate>  
  </Order>  
  <Order>  
    <CustomerID>LETSS</CustomerID>  
    <CompanyName>Let's Stop N Shop</CompanyName>  
    <ContactName>Jaime Yorres</ContactName>  
    <EmployeeID>1</EmployeeID>  
    <OrderDate>1997-06-25T00:00:00</OrderDate>  
  </Order>  
  <Order>  
    <CustomerID>LETSS</CustomerID>  
    <CompanyName>Let's Stop N Shop</CompanyName>  
    <ContactName>Jaime Yorres</ContactName>  
    <EmployeeID>8</EmployeeID>  
    <OrderDate>1997-10-27T00:00:00</OrderDate>  
  </Order>  
  <Order>  
    <CustomerID>LETSS</CustomerID>  
    <CompanyName>Let's Stop N Shop</CompanyName>  
    <ContactName>Jaime Yorres</ContactName>  
    <EmployeeID>6</EmployeeID>  
    <OrderDate>1997-11-10T00:00:00</OrderDate>  
  </Order>  
  <Order>  
    <CustomerID>LETSS</CustomerID>  
    <CompanyName>Let's Stop N Shop</CompanyName>  
    <ContactName>Jaime Yorres</ContactName>  
    <EmployeeID>4</EmployeeID>  
    <OrderDate>1998-02-12T00:00:00</OrderDate>  
  </Order>  
</Root>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [Gelişmiş sorgu teknikleri (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
