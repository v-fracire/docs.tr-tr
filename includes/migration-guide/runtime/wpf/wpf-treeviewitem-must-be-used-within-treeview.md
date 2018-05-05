### <a name="wpf-treeviewitem-must-be-used-within-a-treeview"></a>WPF TreeViewItem TreeView içinde kullanılması gerekir

|   |   |
|---|---|
|Ayrıntılar|Bir değişiklik kullanımını kısıtlar 4.5 içinde sunulan <xref:System.Windows.Controls.TreeViewItem?displayProperty=name> öğeleri dışında bir <xref:System.Windows.Controls.TreeView?displayProperty=name>. Bu, aşağıdaki koşullar altında bildirimleri:<ul><li><xref:System.Windows.Controls.TreeViewItem?displayProperty=name>ın visual üst bir panel değil. (A <xref:System.Windows.Controls.TreeViewItem?displayProperty=name> için oluşturulan bir <xref:System.Windows.Controls.TreeView?displayProperty=name> Masası kendi üst gerekir)</li><li><xref:System.Windows.Controls.TreeViewItem?displayProperty=name> Alt öğesi olan bir <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=name> gören &quot;öğeleri konak&quot; liste denetimi (ListBox, DataGrid, ListView, vb.) için. Sanallaştırma etkinleştirilmesi gerekmez.</li><li><xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=name> Öğesi kaydırma olduğu (<code>ScrollUnit=&quot;Item&quot;</code>).</li><li>Birisi çağırır <code>VirtualizingStackPanel.MakeVisible(v)</code> öğenin kaydırma <code>v</code> gelsin. Bu açık veya örtülü olarak çeşitli şekillerde yapılabilir; belki de en yaygın şekilde yalnızca tıklayarak <code>v</code> klavye odağını vermek için.</li><li>Visual üst zincirinden <code>v</code> için <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=name> geçtiği <xref:System.Windows.Controls.TreeViewItem?displayProperty=name>.</li></ul>Diğer bir deyişle, bu görülür, bir <xref:System.Windows.Controls.TreeViewItem?displayProperty=name> dışında kullanılan bir <xref:System.Windows.Controls.TreeView?displayProperty=name>, ve kullanıcı bir alt öğesi üzerinde <xref:System.Windows.Controls.TreeViewItem?displayProperty=name> görünüme getirmek için. Varsa <xref:System.Windows.Controls.TreeViewItem?displayProperty=name> odaklanabilir hiçbir alt öğelere sahip, bu sorunu hiçbir zaman görürsünüz. Bir örneği burada bu isabet bir durum olduğunda bir <xref:System.Windows.Controls.TreeViewItem?displayProperty=name> DataTemplate köküdür. Bu sorunu gelindiğinde WPF Framework'te oluşan bir InvalidCastException yoktur.|
|Öneri|Bir düzeltme bu kullanıma sunulacaktır.|
|Kapsam|Küçük|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
