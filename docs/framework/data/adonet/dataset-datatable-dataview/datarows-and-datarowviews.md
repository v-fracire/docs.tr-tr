---
title: DataRows ve DataRowViews
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8f5eec26-b809-4aca-8778-7e202356d856
ms.openlocfilehash: 5bd7ebefc03dbe6b44a199ba3123414e7b282c90
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2018
ms.locfileid: "45646814"
---
# <a name="datarows-and-datarowviews"></a>DataRows ve DataRowViews
A <xref:System.Data.DataView> numaralandırılabilir bir topluluğu gösterir <xref:System.Data.DataRowView> nesneleri. **DataRowView** nesneleri adını ya da temel tablodaki sütun sıralı başvurusu tarafından dizine nesne dizileri olarak değerleri göstermek. Erişebildiğiniz <xref:System.Data.DataRow> tarafından sunulan **DataRowView** kullanarak <xref:System.Data.DataRowView.Row%2A> özelliği **DataRowView**.  
  
 Görüntülediğinizde değerleri kullanarak bir **DataRowView**, <xref:System.Data.DataView.RowStateFilter%2A> özelliği **DataView** temel hangi satır sürümünü belirler **DataRow** sunulur. Farklı satır sürümlerini kullanarak erişme hakkında bilgi için bir **DataRow**, bkz: [satır durumları ve satır sürümleri](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).  
  
 Aşağıdaki kod örneği, bir tablodaki tüm geçerli ve orijinal değerleri görüntüler.  
  
```vb  
Dim catView As DataView = New DataView(catDS.Tables("Categories"))  
Console.WriteLine("Current Values:")  
WriteView(catView)  
Console.WriteLine("Original Values:")  
catView.RowStateFilter = DataViewRowState.ModifiedOriginal  
WriteView(catView)      
  
Public Shared Sub WriteView(thisDataView As DataView)  
  Dim rowView As DataRowView  
  Dim i As Integer  
  
  For Each rowView In thisDataView  
    For i = 0 To thisDataView.Table.Columns.Count - 1  
      Console.Write(rowView(i) & vbTab)  
    Next  
    Console.WriteLine()  
  Next  
End Sub  
```  
  
```csharp  
DataView catView = new DataView(catDS.Tables["Categories"]);  
Console.WriteLine("Current Values:");  
WriteView(catView);  
Console.WriteLine("Original Values:");  
catView.RowStateFilter = DataViewRowState.ModifiedOriginal;  
WriteView(catView);  
  
public static void WriteView(DataView thisDataView)  
{  
  foreach (DataRowView rowView in thisDataView)  
  {  
    for (int i = 0; i < thisDataView.Table.Columns.Count; i++)  
      Console.Write(rowView[i] + "\t");  
    Console.WriteLine();  
  }  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Data.DataRowVersion>  
 <xref:System.Data.DataViewRowState>  
 <xref:System.Data.DataView>  
 <xref:System.Data.DataRowView>  
 [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
