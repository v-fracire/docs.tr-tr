---
title: 'Nasıl yapılır: Windows Communication Foundation Güvenlik Olaylarını Denetleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], auditing events
ms.assetid: e71e9587-3336-46a2-9a9e-d72a1743ecec
author: BrucePerlerMS
ms.openlocfilehash: 1efd651751e0f81b5125b64f81f7d2087d002d8d
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47196287"
---
# <a name="how-to-audit-windows-communication-foundation-security-events"></a>Nasıl yapılır: Windows Communication Foundation Güvenlik Olaylarını Denetleme
Windows Communication Foundation (WCF), güvenlik olaylarını Windows olay, Windows Olay Görüntüleyicisi'ni kullanarak görüntüleyebileceğiniz, günlüğüne olanak tanır. Bu konu başlığı altında güvenlik olayları kaydeder, böylece uygulama ayarlama açıklanmaktadır. WCF denetimi hakkında daha fazla bilgi için bkz. [denetim](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
### <a name="to-audit-security-events-in-code"></a>Kod içindeki güvenlik olaylarını denetleme  
  
1.  Denetim günlüğü konumu belirtin. Bunu yapmak için ayarlanmış <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> özelliği <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> sınıfı birine <xref:System.ServiceModel.AuditLogLocation> numaralandırma değerlerinin, aşağıdaki kodda gösterildiği gibi.  
  
     [!code-csharp[AuditingSecurityEvents#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#2)]
     [!code-vb[AuditingSecurityEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#2)]  
  
     <xref:System.ServiceModel.AuditLogLocation> Numaralandırması üç değer vardır: `Application`, `Security`, veya `Default`. Değer günlükleri Olay Görüntüleyicisi'nde görünür birini ya da güvenlik günlüğü veya Uygulama günlüğünü belirtir. Kullanırsanız `Default` değeri, gerçek günlük bağımlı üzerinde uygulamayı çalıştırdığınız işletim sistemi. Etkin denetim ve günlük konumu belirtilmezse, varsayılan değer `Security` günlük yazma desteği sunan platformlar için güvenlik günlüğü için; Aksi takdirde, Yazar `Application` günlük. Yalnızca [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ve [!INCLUDE[wv](../../../../includes/wv-md.md)] varsayılan olarak güvenlik günlüğüne yazma desteği.  
  
2.  Denetlenecek olay türlerini ayarlayın. Aynı anda hizmet düzeyi olayları veya ileti düzeyinde yetkilendirme olayları da denetleyebilirsiniz. Bunu yapmak için ayarlanmış <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> özelliği veya <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> özelliğini birine <xref:System.ServiceModel.AuditLevel> numaralandırma değerlerinin, aşağıdaki kodda gösterildiği gibi.  
  
     [!code-csharp[AuditingSecurityEvents#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#3)]
     [!code-vb[AuditingSecurityEvents#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#3)]  
  
3.  Uygulama günlüğü denetim olaylarını ile ilgili hataları kullanıma sunmak bu seçeneği belirtin. Ayarlama <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> ya da özellik `true` veya `false`aşağıdaki kodda gösterildiği gibi.  
  
     [!code-csharp[AuditingSecurityEvents#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#4)]
     [!code-vb[AuditingSecurityEvents#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#4)]  
  
     Varsayılan `SuppressAuditFailure` özelliği `true`, böylece denetleme hatası uygulamayı etkilemez. Aksi takdirde, bir özel durum oluşturulur. Başarılı bir denetim için bir ayrıntılı izleme yazılır. Denetim herhangi bir hata için izleme hata düzeyinde yazılır.  
  
4.  Var olanı Sil <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> davranışları açıklamada bulunan koleksiyonundan bir <xref:System.ServiceModel.ServiceHost>. Davranış koleksiyon tarafından erişilen <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> karşılık gelen erişilen özelliği <xref:System.ServiceModel.ServiceHostBase.Description%2A> özelliği. Ardından yeni ekleyin <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> aşağıdaki kodda gösterildiği gibi aynı koleksiyonuna.  
  
     [!code-csharp[AuditingSecurityEvents#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#5)]
     [!code-vb[AuditingSecurityEvents#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#5)]  
  
### <a name="to-set-up-auditing-in-configuration"></a>Yapılandırmada denetimini ayarlamak için  
  
1.  Yapılandırmada denetimini ayarlamak için eklemek bir [ \<davranışı >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) öğesine [ \<davranışları >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) web.config dosyasının bölümü. Ardından Ekle bir [ \<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) öğesi ve çeşitli öznitelikler, aşağıdaki örnekte gösterildiği gibi kümesi.  
  
    ```xml  
    <behaviors>  
       <behavior name="myAuditBehavior">  
          <serviceSecurityAudit auditLogLocation="Application"  
                suppressAuditFailure="false"   
                serviceAuthorizationAuditLevel="None"   
                messageAuthenticationAuditLevel="SuccessOrFailure" />  
          </behavior>  
    </behaviors>  
    ```  
  
2.  Aşağıdaki örnekte gösterildiği gibi hizmet davranışı belirtmeniz gerekir.  
  
    ```xml  
    <services>  
        <service type="WCS.Samples.Service.Echo"   
        behaviorConfiguration=" myAuditBehavior">  
           <endpoint address=""  
                    binding="wsHttpBinding"  
                    bindingConfiguration="CertificateDefault"   
                    contract="WCS.Samples.Service.IEcho" />  
        </service>  
    </services>  
    ```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği oluşturur <xref:System.ServiceModel.ServiceHost> sınıfı ve yeni bir ekler <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> davranışları kendi koleksiyonuna.  
  
 [!code-csharp[AuditingSecurityEvents#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#1)]
 [!code-vb[AuditingSecurityEvents#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#1)]  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Ayarı <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> özelliğini `true`, güvenlik denetimleri üretmek için herhangi bir hata bastırır (varsa kümesine `false`, bir özel durum). Ancak, aşağıdaki Windows etkinleştirirseniz **yerel güvenlik ayarları** özelliği, denetim olayları oluşturmak için bir hata neden hemen kapatmak Windows:  
  
 **Güvenlik günlüğü için denetimleri denetim: sistemi hemen kapat**  
  
 Özellik ayarlamak için açık **yerel güvenlik ayarları** iletişim kutusu. Altında **güvenlik ayarları**, tıklayın **yerel ilkeler**. Ardından **güvenlik seçenekleri**.  
  
 Varsa <xref:System.ServiceModel.AuditLogLocation> özelliği <xref:System.ServiceModel.AuditLogLocation.Security> ve **Nesne erişimini denetle** ayarlanmadı **yerel güvenlik ilkesi**, denetim olayları güvenlik günlüğüne değil yazılır. Hiçbir hata döndürdü, ancak denetim girişleri güvenlik günlüğüne yazılmaz unutmayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A>  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>  
 <xref:System.ServiceModel.AuditLogLocation>  
 [Denetim](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)
