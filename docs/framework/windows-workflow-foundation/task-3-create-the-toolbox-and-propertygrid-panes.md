---
title: "Görev 3: PropertyGrid bölmeleri ve araç kutusu oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 72c1546a-eed5-4f0f-a616-719a163414f4
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6896e97a4f9b7625efcef40164c3497ef4f7c90a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="task-3-create-the-toolbox-and-propertygrid-panes"></a>Görev 3: PropertyGrid bölmeleri ve araç kutusu oluşturma
Bu görevde, oluşturacağınız **araç** ve **PropertyGrid** bölmeleri ve bunları rehosted Ekle [!INCLUDE[wfd1](../../../includes/wfd1-md.md)].  
  
 Başvuru için üç tamamladıktan sonra MainWindow.xaml.cs dosyasında olmalıdır kod görevler de [iş akışı Tasarımcısı yeniden barındırılmasını](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md) Konular'a dizi, bu konunun sonunda sağlanır.  
  
### <a name="to-create-the-toolbox-and-add-it-to-the-grid"></a>Araç kutusu oluşturup kılavuza eklemek için  
  
1.  Elde edilen açıklanan yordamı izleyerek HostingApplication projesini açın [görev 2: İş Akışı Tasarımcısı konak](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md).  
  
2.  İçinde **Çözüm Gezgini** bölmesinde MainWindow.xaml dosyasını sağ tıklatın ve seçin **görünümü kodu**.  
  
3.  Ekleme bir `GetToolboxControl` yönteme `MainWindow` oluşturur sınıfı bir <xref:System.Activities.Presentation.Toolbox.ToolboxControl>, yeni bir ekler **araç** kategorisine **araç**ve atar <xref:System.Activities.Statements.Assign> ve <xref:System.Activities.Statements.Sequence> Bu kategori için etkinlik türleri.  
  
    ```csharp  
    private ToolboxControl GetToolboxControl()  
    {  
        // Create the ToolBoxControl.  
        ToolboxControl ctrl = new ToolboxControl();  
  
        // Create a category.  
        ToolboxCategory category = new ToolboxCategory("category1");  
  
        // Create Toolbox items.  
        ToolboxItemWrapper tool1 =   
            new ToolboxItemWrapper("System.Activities.Statements.Assign",   
            typeof(Assign).Assembly.FullName, null, "Assign");  
  
        ToolboxItemWrapper tool2 = new ToolboxItemWrapper("System.Activities.Statements.Sequence",   
            typeof(Sequence).Assembly.FullName, null, "Sequence");  
  
        // Add the Toolbox items to the category.  
        category.Add(tool1);  
        category.Add(tool2);  
  
        // Add the category to the ToolBox control.  
        ctrl.Categories.Add(category);  
        return ctrl;  
    }  
    ```  
  
4.  Özel eklemek `AddToolbox` yönteme `MainWindow` yerleştirir sınıfı **araç** kılavuzundaki sol sütunda.  
  
    ```csharp  
    private void AddToolBox()  
    {  
        ToolboxControl tc = GetToolboxControl();  
        Grid.SetColumn(tc, 0);  
        grid1.Children.Add(tc);  
    }  
    ```  
  
5.  Bir çağrı ekleyin `AddToolBox` yönteminde `MainWindow()` aşağıdaki kodda gösterildiği gibi sınıfı oluşturucusu.  
  
    ```csharp  
    public MainWindow()  
    {  
        InitializeComponent();  
        this.RegisterMetadata();  
        this.AddDesigner();  
  
        this.AddToolBox();  
    }  
    ```  
  
6.  Derleme ve çözümünüzü çalıştırmak için F5 tuşuna basın. **Araç** içeren <xref:System.Activities.Statements.Assign> ve <xref:System.Activities.Statements.Sequence> etkinlikleri görüntülenmesi.  
  
### <a name="to-create-the-propertygrid"></a>PropertyGrid oluşturmak için  
  
1.  İçinde **Çözüm Gezgini** bölmesinde MainWindow.xaml dosyasını sağ tıklatın ve seçin **görünümü kodu**.  
  
2.  Ekleme `AddPropertyInspector` yönteme `MainWindow` yerleştirmek için sınıf **PropertyGrid** kılavuzundaki en sağdaki sütun bölmesinde.  
  
    ```csharp  
    private void AddPropertyInspector()  
    {  
        Grid.SetColumn(wd.PropertyInspectorView, 2);  
        grid1.Children.Add(wd.PropertyInspectorView);              
    }  
    ```  
  
3.  Bir çağrı ekleyin `AddPropertyInspector` yönteminde `MainWindow()` aşağıdaki kodda gösterildiği gibi sınıfı oluşturucusu.  
  
    ```csharp  
    public MainWindow()  
    {  
        InitializeComponent();  
        this.RegisterMetadata();  
        this.AddDesigner();  
        this.AddToolBox();  
  
        this.AddPropertyInspector();   
    }  
    ```  
  
4.  Derleme ve çözümü çalıştırmak için F5 tuşuna basın. **Araç**, iş akışı tasarım tuvale ve **PropertyGrid** bölmeleri tüm görüntülenmesi ve sürüklediğinizde bir <xref:System.Activities.Statements.Assign> etkinlik veya <xref:System.Activities.Statements.Sequence> tasarım tuvale etkinliği Özellik Kılavuzu vurgulanan etkinlik bağlı olarak güncelleştirmeniz gerekir.  
  
## <a name="example"></a>Örnek  
 MainWindow.xaml.cs dosya artık aşağıdaki kodu içermelidir.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Windows;  
using System.Windows.Controls;  
using System.Windows.Data;  
using System.Windows.Documents;  
using System.Windows.Input;  
using System.Windows.Media;  
using System.Windows.Media.Imaging;  
using System.Windows.Navigation;  
using System.Windows.Shapes;  
//dlls added  
using System.Activities;  
using System.Activities.Core.Presentation;  
using System.Activities.Presentation;  
using System.Activities.Presentation.Metadata;  
using System.Activities.Presentation.Toolbox;  
using System.Activities.Statements;  
using System.ComponentModel;  
  
namespace HostingApplication  
{  
    /// <summary>  
    /// Interaction logic for MainWindow.xaml  
    /// </summary>  
    public partial class MainWindow : Window  
    {  
        private WorkflowDesigner wd;  
  
        public MainWindow()  
        {  
            InitializeComponent();  
            RegisterMetadata();  
            AddDesigner();  
            this.AddToolBox();  
            this.AddPropertyInspector();  
        }  
  
        private void AddDesigner()  
        {  
            //Create an instance of WorkflowDesigner class.  
            this.wd = new WorkflowDesigner();  
  
            //Place the designer canvas in the middle column of the grid.  
            Grid.SetColumn(this.wd.View, 1);  
  
            //Load a new Sequence as default.  
            this.wd.Load(new Sequence());  
  
            //Add the designer canvas to the grid.  
            grid1.Children.Add(this.wd.View);  
        }  
  
        private void RegisterMetadata()  
        {  
            DesignerMetadata dm = new DesignerMetadata();  
            dm.Register();  
        }  
  
        private ToolboxControl GetToolboxControl()  
        {  
            // Create the ToolBoxControl.  
            ToolboxControl ctrl = new ToolboxControl();  
  
            // Create a category.  
            ToolboxCategory category = new ToolboxCategory("category1");  
  
            // Create Toolbox items.  
            ToolboxItemWrapper tool1 =  
                new ToolboxItemWrapper("System.Activities.Statements.Assign",  
                typeof(Assign).Assembly.FullName, null, "Assign");  
  
            ToolboxItemWrapper tool2 = new ToolboxItemWrapper("System.Activities.Statements.Sequence",  
                typeof(Sequence).Assembly.FullName, null, "Sequence");  
  
            // Add the Toolbox items to the category.  
            category.Add(tool1);  
            category.Add(tool2);  
  
            // Add the category to the ToolBox control.  
            ctrl.Categories.Add(category);  
            return ctrl;  
        }  
  
        private void AddToolBox()  
        {  
            ToolboxControl tc = GetToolboxControl();  
            Grid.SetColumn(tc, 0);  
            grid1.Children.Add(tc);  
        }  
  
        private void AddPropertyInspector()  
        {  
            Grid.SetColumn(wd.PropertyInspectorView, 2);  
            grid1.Children.Add(wd.PropertyInspectorView);  
        }  
  
    }  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İş Akışı Tasarımcısı yeniden barındırma](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)  
 [Görev 1: yeni bir Windows Presentation Foundation uygulaması oluşturma](../../../docs/framework/windows-workflow-foundation/task-1-create-a-new-wpf-app.md)  
 [Görev 2: ana bilgisayar iş akışı Tasarımcısı](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md)