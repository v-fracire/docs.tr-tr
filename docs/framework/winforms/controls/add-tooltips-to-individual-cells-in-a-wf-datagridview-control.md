---
title: "Nasıl yapılır: Bir Windows Forms DataGridView Denetiminde Ayrı Hücrelere ToolTips Ekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], adding to data grids
- DataGridView control [Windows Forms], adding tooltips
- data grids [Windows Forms], adding tooltips
ms.assetid: 2a81f9de-d58b-4ea8-bc0b-8d93c2f4cf78
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 73d12bb38e4929582a8317d8ab3d7b23a7d1f603
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-tooltips-to-individual-cells-in-a-windows-forms-datagridview-control"></a>Nasıl yapılır: Bir Windows Forms DataGridView Denetiminde Ayrı Hücrelere ToolTips Ekleme
Varsayılan olarak, araç ipuçları değerlerini görüntülemek için kullanılan <xref:System.Windows.Forms.DataGridView> tüm içerikleri göstermek için çok küçük olan hücre. Ancak, tek tek hücreler için araç ipucu metni değerlerini ayarlamak için bu davranış kılabilirsiniz. Bu, kullanıcıların bir hücre hakkında ek bilgi görüntülemek için veya alternatif bir açıklama hücre içeriğinin kullanıcılara sağlamak için kullanışlıdır. Örneğin, durum simgelerini görüntüleyen bir satır varsa, araç ipuçları kullanma metin açıklamaları sağlamak isteyebilirsiniz.  
  
 Ayarlayarak da hücre düzeyi ipuçlarını görüntülemeyi devre dışı bırakabilirsiniz <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType> özelliğine `false`.  
  
### <a name="to-add-a-tooltip-to-a-cell"></a>Bir araç ipucu bir hücreye eklemek için  
  
-   Ayarlama <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType> özelliği.  
  
     [!code-cpp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/cpp/datagridviewcell.tooltiptext.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/CS/datagridviewcell.tooltiptext.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridViewCell.ToolTipText#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/VB/datagridviewcell.tooltiptext.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-   Bu örnek gerektirir:  
  
-   A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1` adlı bir sütun içeren `Rating` dört yıldız aracılığıyla bir dize değerini görüntülemek için ("*") simgeler. <xref:System.Windows.Forms.DataGridView.CellFormatting> Denetiminin olayı olmalıdır ilişkili örnekte gösterilen olay işleyicisi yöntemi ile.  
  
-   Başvurular <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Bağladığınızda <xref:System.Windows.Forms.DataGridView> denetlemek için dış veri kaynağına veya sanal modu uygulama tarafından kendi veri kaynağı sağlamak, performans sorunlarla karşılaşabilirsiniz. Büyük miktarlarda veri çalışırken performans cezası önlemek için tanıtıcı <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> ayarı yerine olay <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> birden çok hücreyi özelliği. Ne zaman, tanıtıcı bu olay bir hücrenin değerini alma <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> özelliği olayını başlatır ve değerini döndürür <xref:System.Windows.Forms.DataGridViewCellToolTipTextNeededEventArgs.ToolTipText%2A?displayProperty=nameWithType> özelliği olarak belirtilen olay işleyicisi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCell>  
 <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType>  
 [Hücrelerini, satırları ve sütunları Windows Forms DataGridView denetiminde ile programlama](../../../../docs/framework/winforms/controls/programming-with-cells-rows-and-columns-in-the-datagrid.md)