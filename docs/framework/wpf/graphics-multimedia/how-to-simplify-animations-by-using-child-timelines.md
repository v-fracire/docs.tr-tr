---
title: 'Nasıl yapılır: Alt Öğe Zaman Çizelgelerini Kullanarak Animasyonları Basitleştirme'
ms.date: 03/30/2017
helpviewer_keywords:
- simplifying animations by child timelines [WPF]
- animation [WPF], simplifying by child timelines
- child timelines [WPF]
ms.assetid: 8335d770-d13d-42bd-8dfa-63f92c0327e2
ms.openlocfilehash: 57ea558b167f647ec7597ba95382abb0e48f699f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561679"
---
# <a name="how-to-simplify-animations-by-using-child-timelines"></a>Nasıl yapılır: Alt Öğe Zaman Çizelgelerini Kullanarak Animasyonları Basitleştirme
Bu örnek alt kullanarak animasyonları basitleştirme gösterilmektedir <xref:System.Windows.Media.Animation.ParallelTimeline> nesneleri. A <xref:System.Windows.Media.Animation.Storyboard> bir tür <xref:System.Windows.Media.Animation.Timeline> içerdiği zaman çizelgeleri için hedefleme bilgileri sağlar. Kullanım bir <xref:System.Windows.Media.Animation.Storyboard> nesne ve özellik bilgileri de dahil olmak üzere, zaman çizelgesi hedeflemesi bilgilerini sağlamak için.  
  
 Bir animasyon başlamak için bir veya daha fazla kullanın <xref:System.Windows.Media.Animation.ParallelTimeline> nesneleri iç içe alt öğeleri olarak bir <xref:System.Windows.Media.Animation.Storyboard>. Bunlar <xref:System.Windows.Media.Animation.ParallelTimeline> nesneleri diğer animasyonları içerebilir ve bu nedenle, karmaşık bir animasyon zamanlama sıralarında daha iyi yerleştirebilirsiniz. Örneğin, animasyonu yapıyorsanız bir <xref:System.Windows.Controls.TextBlock> ve aynı çeşitli şekillerde <xref:System.Windows.Media.Animation.Storyboard>, animasyonlarını ayırabilirsiniz <xref:System.Windows.Controls.TextBlock> ve her bir ayrı koyma şekiller <xref:System.Windows.Media.Animation.ParallelTimeline>. Çünkü her <xref:System.Windows.Media.Animation.ParallelTimeline> kendi <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> ve tüm alt öğeleri <xref:System.Windows.Media.Animation.ParallelTimeline> bu göreli başlamak <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>, zamanlama daha iyi kapsüllenir.  
  
 Aşağıdaki örnekte iki parça metin canlandırır (<xref:System.Windows.Controls.TextBlock> nesneler) gelen aynı içinde <xref:System.Windows.Media.Animation.Storyboard>. A <xref:System.Windows.Media.Animation.ParallelTimeline> birindeki animasyonları yalıtır <xref:System.Windows.Controls.TextBlock> nesneleri.  
  
 **Performans Not:** geçirebilmenize karşın <xref:System.Windows.Media.Animation.Storyboard> zaman çizelgelerini birbirlerine iç <xref:System.Windows.Media.Animation.ParallelTimeline>lar daha az ek yük gerektirdiğinden, iç içe geçme daha uygundur. ( <xref:System.Windows.Media.Animation.Storyboard> Sınıfının devraldığı <xref:System.Windows.Media.Animation.ParallelTimeline> sınıfı.)  
  
## <a name="example"></a>Örnek  
 [!code-xaml[Timelines_snip#ParallelTimelineWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Timelines_snip/CS/ParallelTimelineExample.xaml#paralleltimelinewholepage)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Animasyona Genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Görsel Taslak Animasyonları Arasında HandoffBehavior Belirtme](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-handoffbehavior-between-storyboard-animations.md)
