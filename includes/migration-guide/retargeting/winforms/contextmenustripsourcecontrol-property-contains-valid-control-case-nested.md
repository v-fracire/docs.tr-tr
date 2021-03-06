### <a name="contextmenustripsourcecontrol-property-contains-a-valid-control-in-the-case-of-nested-toolstripmenuitems"></a>İç içe geçmiş Toolstripmenuıtems söz konusu olduğunda, geçerli bir denetim ContextMenuStrip.SourceControl özelliği içerir

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.7.1 ve önceki sürümlerde <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> özelliği yanlış menüden kullanıcı oturum açtığında null döndürür iç içe geçmiş <xref:System.Windows.Forms.ToolStripMenuItem> kontrol eder. .NET Framework'teki 4.7.2 ve daha sonra <xref:System.Windows.Forms.ContextMenuStrip.SourceControl> özelliği her zaman gerçek kaynak denetimine ayarlayın.|
|Öneri|<strong>İçine veya dışına bu değişiklikleri nasıl</strong>sırada bu değişiklikleri yararlanmak bir uygulama için .NET Framework 4.7.2 çalıştırmanız gerekir veya üzeri. Uygulamaya bu değişiklikler aşağıdaki yollardan birini yararlanabilir:<ul><li>Bu, .NET Framework 4.7.2 hedefler. Bu, varsayılan olarak .NET Framework'ü 4.7.2 hedefleyen Windows Forms uygulamaları etkin ya da üzeri değişikliktir.</li><li>.NET Framework 4.7.1 veya önceki bir sürümünü hedefleyen ve eski erişilebilirlik davranışları dışında aşağıdakileri ekleyerek bölgedeyse [AppContext anahtar](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) için <code>&lt;runtime&gt;</code> app.config dosyası ve içinayarlamabölümünü<code>false</code>aşağıdaki örnekte gösterildiği gibi.</li></ul><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>.NET Framework 4.7.2 hedefleyen uygulamalar veya sonraki bir sürümü ve eski korumak istediğiniz davranışı kabul etme eski tip bir kaynak denetim değerini kullanımını açıkça ayarlayarak bu AppContext anahtar <code>true</code>.|
|Kapsam|Kenar|
|Sürüm|4.7.2|
|Tür|Yeniden hedefleme|
|Etkilenen API'leri|<ul><li><xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType></li></ul>|

