---
title: 'Nasıl yapılır: Basit veya Karmaşık TreeViews Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- TreeView control [WPF], creating
- Control class [WPF], TreeView [WPF], creating
ms.assetid: 1defbb78-b8e7-4c0e-b650-576453ac828d
ms.openlocfilehash: 54e9218ea1460a0c29d8b9d7b9c740c18ac7ab24
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33553004"
---
# <a name="how-to-create-simple-or-complex-treeviews"></a>Nasıl yapılır: Basit veya Karmaşık TreeViews Oluşturma
Bu örnekte basit veya karmaşık oluşturulacağını gösterir <xref:System.Windows.Controls.TreeView> kontrol eder.  
  
 A <xref:System.Windows.Controls.TreeView> bir hiyerarşisinden oluşur <xref:System.Windows.Controls.TreeViewItem> basit metin dizelerini ve ayrıca daha karmaşık içerik gibi içerebilir denetimleri <xref:System.Windows.Controls.Button> denetimleri veya <xref:System.Windows.Controls.StackPanel> katıştırılmış içeriğe sahip. Açıkça tanımlayabilirsiniz <xref:System.Windows.Controls.TreeView> içerik veya bir veri kaynağı içeriği sağlayabilir. Bu konu bu kavramların örneklerini sağlar.  
  
## <a name="example"></a>Örnek  
 <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> Özelliği <xref:System.Windows.Controls.TreeViewItem> içeriği, <xref:System.Windows.Controls.TreeView> bu öğe için görüntüler. A <xref:System.Windows.Controls.TreeViewItem> da sahip olabilirsiniz <xref:System.Windows.Controls.TreeViewItem> ve alt öğeleri olarak denetimleri kullanarak bu alt öğeleri tanımlayabilirsiniz <xref:System.Windows.Controls.ItemsControl.Items%2A> özelliği.  
  
 Aşağıdaki örnek açıkça nasıl tanımlanacağı gösterilmektedir <xref:System.Windows.Controls.TreeViewItem> ayarlayarak içerik <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> özelliği için bir metin dizesi.  
  
 [!code-xaml[TreeViewSimple#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#1)]  
  
 Aşağıdaki örnek Göster alt öğeleri tanımlamak nasıl bir <xref:System.Windows.Controls.TreeViewItem> tanımlayarak <xref:System.Windows.Controls.ItemsControl.Items%2A> olan <xref:System.Windows.Controls.Button> kontrol eder.  
  
 [!code-xaml[TreeViewSimple#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#3)]  
  
 Aşağıdaki örnekte nasıl oluşturulacağını gösterir bir <xref:System.Windows.Controls.TreeView> burada bir <xref:System.Windows.Data.XmlDataProvider> sağlar <xref:System.Windows.Controls.TreeViewItem> içerik ve <xref:System.Windows.HierarchicalDataTemplate> içeriğinin görünümünü tanımlar.  
  
 [!code-xaml[TreeViewSimple#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#6)]  
  
 [!code-xaml[TreeViewSimple#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#7)]  
  
 [!code-xaml[TreeViewSimple#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#5)]  
  
 Aşağıdaki örnekte nasıl oluşturulacağını gösterir bir <xref:System.Windows.Controls.TreeView> nerede <xref:System.Windows.Controls.TreeViewItem> içeriği <xref:System.Windows.Controls.DockPanel> katıştırılmış içeriğe sahip kontrol eder.  
  
 [!code-xaml[TreeViewSimple#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#9)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.TreeView>  
 <xref:System.Windows.Controls.TreeViewItem>  
 [TreeView Genel Bakış](../../../../docs/framework/wpf/controls/treeview-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/controls/treeview-how-to-topics.md)
