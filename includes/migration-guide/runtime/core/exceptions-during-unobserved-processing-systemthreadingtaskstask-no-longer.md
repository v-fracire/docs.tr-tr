### <a name="exceptions-during-unobserved-processing-in-systemthreadingtaskstask-no-longer-propagate-on-finalizer-thread"></a>Sonlandırıcı iş parçacığında unobserved işlemede System.Threading.Tasks.Task artık sırasında özel durumlar yayma

|   |   |
|---|---|
|Ayrıntılar|Çünkü <xref:System.Threading.Tasks.Task?displayProperty=name> sınıfı temsil eder, zaman uyumsuz bir işlem, zaman uyumsuz işlem sırasında oluşan tüm ciddi olmayan özel durumları yakalar. .NET Framework 4.5, özel bir durum değil gözlenir ve kodunuzu hiçbir zaman görevi bekler, özel durum artık sonlandırıcıyı parçacığında yaymak ve atık toplama sırasında işlem kilitlenme. Bu değişiklik görevi sınıfı unobserved zaman uyumsuz işleme gerçekleştirmek için kullandığınız uygulamalarının güvenilirliğini artırır.|
|Öneri|Bir uygulama sonlandırıcıyı iş parçacığına yayılıyor unobserved zaman uyumsuz özel durumları bağlıdır, önceki davranış için uygun bir işleyiciyi sağlayarak geri yüklenebilir <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> olayı veya ayarlayarak bir [çalışma zamanı yapılandırma öğesi ](~/docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md).|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run(System.Action,System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run(System.Func{System.Threading.Tasks.Task})?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run(System.Func{System.Threading.Tasks.Task},System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run%60%601(System.Func{%60%600})?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run%60%601(System.Func{%60%600},System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run%60%601(System.Func{System.Threading.Tasks.Task{%60%600}})?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run%60%601(System.Func{System.Threading.Tasks.Task{%60%600}},System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Start?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Start(System.Threading.Tasks.TaskScheduler)?displayProperty=nameWithType></li></ul>|
