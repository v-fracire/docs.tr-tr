---
title: "Bağlamalar ve Güvenlik"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- bindings [WCF], security
- WCF security
- Windows Communication Foundation, security
- bindings [WCF]
ms.assetid: 4de03dd3-968a-4e65-af43-516e903d7f95
caps.latest.revision: "42"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 9a6ba021688094afcbbb176cf03fb3e4b4c10df7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="bindings-and-security"></a>Bağlamalar ve Güvenlik
İle birlikte gelen sistem tarafından sağlanan bağlamalar [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] program hızlı bir şekilde sunma [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulamalar. Bunun tek istisnası etkin bir varsayılan güvenlik düzeni tüm bağlamaları vardır. Bu konuda, güvenlik ihtiyaçlarınızı için doğru bağlama seçmenize yardımcı olur.  
  
 Genel Bakış [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] güvenlik, bkz: [güvenliğine genel bakış](../../../../docs/framework/wcf/feature-details/security-overview.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]programlama [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bağlamalar kullanılarak, bkz: [WCF güvenliğini programlama](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md).  
  
 Bir bağlama seçtiyseniz, güvenlik ile ilişkili çalışma zamanı davranışı hakkında daha fazla bilgi bulabilirsiniz [güvenlik davranışları](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md).  
  
 Bazı güvenlik işlevleri sistem tarafından sağlanan bağlamalar kullanılarak programlanabilir değildir. Özel bağlama kullanma daha fazla denetim için bkz: [özel bağlamalarla güvenlik özellikleri](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md).  
  
## <a name="security-functions-of-bindings"></a>Güvenlik işlevlerini bağlamaları  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Çoğu gereksinimlerini karşılayacak sistem tarafından sağlanan bağlamalar sayısını içerir. Belirli bir bağlama yeterli değil, özel bağlama de oluşturabilirsiniz. Sistem tarafından sağlanan bağlamalar listesi için bkz: [System-Provided bağlamaları](../../../../docs/framework/wcf/system-provided-bindings.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Özel bağlamalar bkz [özel bağlamalar](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
 Her bağlama [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iki tür vardır: bir API ve bir yapılandırma dosyasında kullanılan bir XML öğesi olarak. Örneğin, `WSHttpBinding` (API) sahip bir karşılık gelen [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).  
  
 Aşağıdaki bölümde her bağlama için her iki formları listeler ve güvenlik özellikleri özetlenmektedir.  
  
### <a name="basichttp"></a>BasicHttp  
 Kod içinde kullanma <xref:System.ServiceModel.BasicHttpBinding> sınıf; yapılandırmasında kullanmasına [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).  
  
 Bu bağlama mevcut teknolojiler, aşağıdakiler de dahil olmak üzere çeşitli ile kullanılmak üzere tasarlanmıştır:  
  
-   ASP.NET Web Hizmetleri (ASMX), sürüm 1.  
  
-   Web hizmeti Enhancements (WSE) uygulamaları.  
  
-   Web Hizmetleri birlikte çalışabilirlik tanımlandığı gibi temel profil (WS-ı) belirtimi ([http://go.microsoft.com/fwlink/?LinkId=38955](http://go.microsoft.com/fwlink/?LinkId=38955)).  
  
-   WS içinde tanımlanan temel güvenlik profili-ı.  
  
 Varsayılan olarak, bu bağlantı güvenli değil. ASMX Hizmetleri ile birlikte çalışmak üzere tasarlanmıştır. Güvenlik etkinleştirildiğinde, bağlama temel kimlik doğrulaması, Özet ve tümleşik Windows güvenliği gibi Internet Information Services (IIS) güvenlik mekanizmaları ile sorunsuz birlikte çalışma için tasarlanmıştır. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Taşıma güvenliği genel bakış](../../../../docs/framework/wcf/feature-details/transport-security-overview.md). Bu bağlama aşağıdakileri destekler:  
  
-   HTTPS taşıma güvenliği.  
  
-   HTTP temel kimlik doğrulaması.  
  
-   WS-güvenliği.  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<xref:System.ServiceModel.BasicHttpSecurity>, <xref:System.ServiceModel.BasicHttpMessageSecurity>, <xref:System.ServiceModel.BasicHttpMessageCredentialType>, ve <xref:System.ServiceModel.BasicHttpSecurityMode>.  
  
### <a name="wshttpbinding"></a>WSHttpBinding  
 Kod içinde kullanma <xref:System.ServiceModel.WSHttpBinding> sınıf; yapılandırmasında kullanmasına [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).  
  
 Varsayılan olarak, bu bağlama WS-Security belirtimi uygular ve WS - uygulayan Hizmetleri ile birlikte çalışabilirlik sağlar * belirtimleri. Aşağıdakileri destekler:  
  
-   HTTPS taşıma güvenliği.  
  
-   WS-güvenliği.  
  
-   HTTPS koruma SOAP iletisi kimlik bilgisi güvenlik arayan kimlik doğrulaması için taşıma.  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<xref:System.ServiceModel.WSHttpSecurity>, <xref:System.ServiceModel.MessageSecurityOverHttp>, <xref:System.ServiceModel.MessageCredentialType>, <xref:System.ServiceModel.SecurityMode>, <xref:System.ServiceModel.HttpTransportSecurity>, <xref:System.ServiceModel.HttpClientCredentialType>, ve <xref:System.ServiceModel.HttpProxyCredentialType>.  
  
### <a name="wsdualhttpbinding"></a>WSDualHttpBinding  
 Kod içinde kullanma <xref:System.ServiceModel.WSDualHttpBinding> sınıf; yapılandırmasında kullanmasına [ \<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).  
  
 Bu bağlama, çift yönlü hizmet uygulamaları sağlamak için tasarlanmıştır. Bu bağlama aktarımı ileti tabanlı güvenlik için WS-Security belirtimi uygular. Taşıma güvenliği kullanılamıyor. Varsayılan olarak, aşağıdaki özellikleri sağlar:  
  
-   WS güvenilir Mesajlaşma güvenilirliği uygular.  
  
-   WS güvenliği aktarımı güvenlik ve kimlik doğrulaması için uygular.  
  
-   HTTP ileti teslimi için kullanır.  
  
-   İleti Text/XML kodlama kullanır.  
  
 WS-Security (ileti Katmanı Güvenliği) kullanılarak, bağlama, aşağıdaki parametreleri yapılandırmanıza olanak sağlar:  
  
-   Şifreleme algoritması belirlemek için Güvenlik algoritması paketi.  
  
-   Aşağıdaki seçenekler bağlama:  
  
    -   Hizmet kimlik bilgilerini kullanılabilir-bant istemcide sağlama.  
  
    -   Kanal kurulumunun bir parçası olarak hizmetinden hizmet kimlik bilgilerini sağlayan anlaşma.  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<xref:System.ServiceModel.WSDualHttpSecurity> ve <xref:System.ServiceModel.WSDualHttpSecurityMode>.  
  
### <a name="nettcpbinding"></a>NetTcpBinding  
 Kod içinde kullanma <xref:System.ServiceModel.NetTcpBinding> sınıf; yapılandırmasında kullanmasına [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).  
  
 Bu bağlama, makineler arası iletişim için optimize edilmiştir. Varsayılan olarak, aşağıdaki özelliklere sahiptir:  
  
-   Aktarım Katmanı Güvenliği uygular.  
  
-   Windows güvenliği aktarımı güvenlik ve kimlik doğrulama için yararlanır.  
  
-   TCP taşıma için kullanır.  
  
-   Implements ikili ileti kodlama.  
  
-   Implements WS güvenilir Mesajlaşma.  
  
 Seçenekler aşağıdakileri içerir:  
  
-   İleti Katmanı Güvenliği (WS-güvenlik kullanarak).  
  
-   Aktarım ileti kimlik bilgileri ile güvenliği — gizliliği ve bütünlük Aktarım Katmanı Güvenliği (TLS) tarafından WS-Security tarafından sağlanan yetkilendirme için TCP ve kimlik bilgileri sağlanan.  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<xref:System.ServiceModel.NetTcpSecurity>, <xref:System.ServiceModel.TcpTransportSecurity>, <xref:System.ServiceModel.TcpClientCredentialType>, <xref:System.ServiceModel.MessageSecurityOverTcp>, ve <xref:System.ServiceModel.MessageCredentialType>.  
  
### <a name="netnamedpipebinding"></a>NetNamedPipeBinding  
 Kod içinde kullanma <xref:System.ServiceModel.NetNamedPipeBinding> sınıf; yapılandırmasında kullanmasına [ \<netNamedPipeBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).  
  
 Bu bağlama, işlem içi iletişimi (genellikle aynı makine üzerindeki) için optimize edilmiştir. Varsayılan olarak, bu bağlama aşağıdaki özelliklere sahiptir:  
  
-   Aktarım güvenliği ileti aktarma ve kimlik doğrulaması için kullanır.  
  
-   İleti teslimi için adlandırılmış kanallar kullanır.  
  
-   Implements ikili ileti kodlama.  
  
-   Şifreleme ve ileti imzalama.  
  
 Seçenekler aşağıdakileri içerir:  
  
-   Windows güvenliği kullanarak kimlik doğrulaması.  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<xref:System.ServiceModel.NetNamedPipeSecurity>, <xref:System.ServiceModel.NetNamedPipeSecurityMode>, ve <xref:System.ServiceModel.NamedPipeTransportSecurity>.  
  
### <a name="msmqintegrationbinding"></a>MsmqIntegrationBinding  
 Kod içinde kullanma <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> sınıf; yapılandırmasında kullanmasına [ \<MsmqIntegrationBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md).  
  
 Bu bağlama oluşturmak için optimize edilmiştir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemciler ve olmayan ile birlikte Hizmetler[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Microsoft Message Queuing (MSMQ) uç noktaları.  
  
 Varsayılan olarak, bu bağlama taşıma güvenliği kullanır ve aşağıdaki güvenlik özellikleri sağlar:  
  
-   Güvenlik olabilir (hiçbiri) devre dışı.  
  
-   MSMQ taşıma güvenliği (aktarım).  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<xref:System.ServiceModel.NetMsmqSecurity> ve <xref:System.ServiceModel.NetMsmqSecurityMode>.  
  
### <a name="netmsmqbinding"></a>NetMsmqBinding  
 Kod içinde kullanma <xref:System.ServiceModel.NetMsmqBinding> sınıf; yapılandırmasında kullanmasına [ \<netMsmqBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md).  
  
 Bu bağlama oluştururken kullanılması amaçlanmıştır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] MSMQ gerektiren hizmetleri kuyruğa ileti desteği.  
  
 Varsayılan olarak, bu bağlama taşıma güvenliği kullanır ve aşağıdaki güvenlik özellikleri sağlar:  
  
-   Güvenlik olabilir (hiçbiri) devre dışı.  
  
-   MSMQ taşıma güvenliği (aktarım).  
  
-   SOAP tabanlı ileti güvenliği (ileti).  
  
-   Eşzamanlı aktarım ve ileti güvenliği (her ikisi de).  
  
-   İstemci kimlik bilgisi desteklenen türler: None, Windows, kullanıcı adı, sertifika, IssuedToken.  
  
 <xref:System.ServiceModel.MessageCredentialType.Certificate> Kimlik bilgisi yalnızca güvenlik modu olarak ayarlandığında desteklenir <xref:System.ServiceModel.NetMsmqSecurityMode.Both> veya <xref:System.ServiceModel.NetMsmqSecurityMode.Message>.  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<xref:System.ServiceModel.MessageSecurityOverMsmq> ve <xref:System.ServiceModel.MsmqTransportSecurity>.  
  
### <a name="wsfederationhttpbinding"></a>WSFederationHttpBinding  
 Kod içinde kullanma <xref:System.ServiceModel.WSFederationHttpBinding> sınıf; yapılandırmasında kullanmasına [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).  
  
 Varsayılan olarak, bu bağlama WS-Security (ileti Katmanı Güvenliği) kullanır.  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Federasyon](../../../../docs/framework/wcf/feature-details/federation.md), <xref:System.ServiceModel.WSFederationHttpSecurity>, ve <xref:System.ServiceModel.WSFederationHttpSecurityMode>.  
  
## <a name="custom-bindings"></a>Özel Bağlamalar  
 Sistem tarafından sağlanan bağlamalar hiçbiri gereksinimlerini karşılayıp karşılamadığını olan bir özel güvenlik bağlama öğesi özel bağlama oluşturabilirsiniz. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Özel bağlamalarla güvenlik özellikleri](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md).  
  
## <a name="binding-choices"></a>Seçimler bağlama  
 Güvenlik Modu ayarını sunulan özellikler aşağıdaki tabloda özetlenmiştir, diğer bir deyişle, güvenlik modu ayarlandığında kullanılabilen özellikleri listeler `Transport`, `Message`, veya `TransportWithMessageCredential`. Uygulamanızın gerektirdiği güvenlik özellikleri bulmanıza yardımcı olmak için bu tabloyu kullanın.  
  
|Ayar|Özellikler|  
|-------------|--------------|  
|Taşıma|Sunucu kimlik doğrulaması<br /><br /> İstemci kimlik doğrulaması<br /><br /> Noktadan noktaya güvenlik<br /><br /> Birlikte Çalışabilirlik<br /><br /> Donanım hızlandırma<br /><br /> Yüksek verimlilik<br /><br /> Güvenli güvenlik duvarı<br /><br /> Yüksek gecikmeli uygulamaları<br /><br /> Birden çok atlama arasında yeniden şifreleme|  
|İleti|Sunucu kimlik doğrulaması<br /><br /> İstemci kimlik doğrulaması<br /><br /> Uçtan uca güvenlik<br /><br /> Birlikte Çalışabilirlik<br /><br /> Zengin talepleri<br /><br /> Federasyon<br /><br /> Çok faktörlü kimlik doğrulama<br /><br /> Özel belirteçler<br /><br /> Notary/zaman damgası hizmeti<br /><br /> Yüksek gecikmeli uygulamaları<br /><br /> İleti imzalarını kalıcılığı|  
|TransportWithMessageCredential|Sunucu kimlik doğrulaması<br /><br /> İstemci kimlik doğrulaması<br /><br /> Noktadan noktaya güvenlik<br /><br /> Birlikte Çalışabilirlik<br /><br /> Donanım hızlandırma<br /><br /> Yüksek verimlilik<br /><br /> Zengin istemci talepleri<br /><br /> Federasyon<br /><br /> Çok faktörlü kimlik doğrulama<br /><br /> Özel belirteçler<br /><br /> Güvenli güvenlik duvarı<br /><br /> Yüksek gecikmeli uygulamaları<br /><br /> Birden çok atlama arasında yeniden şifreleme|  
  
 Aşağıdaki tabloda, çeşitli modu ayarları destekleyen bağlamaları listeler. Bir bağlama Hizmeti uç noktası oluşturmak için kullanılacak tablosundan seçin.  
  
|Bağlama|Aktarım modu desteği|İleti modu desteği|TransportWithMessageCredential desteği|  
|-------------|----------------------------|--------------------------|--------------------------------------------|  
|`BasicHttpBinding`|Evet|Evet|Evet|  
|`WSHttpBinding`|Evet|Evet|Evet|  
|`WSDualHttpBinding`|Hayır|Evet|Hayır|  
|`NetTcpBinding`|Evet|Evet|Evet|  
|`NetNamedPipeBinding`|Evet|Hayır|Hayır|  
|`NetMsmqBinding`|Evet|Evet|Hayır|  
|`MsmqIntegrationBinding`|Evet|Hayır|Hayır|  
|`wsFederationHttpBinding`|Hayır|Evet|Evet|  
  
## <a name="transport-credentials-in-bindings"></a>Bağlamaları taşıma kimlik bilgileri  
 Aşağıdaki tabloda kullanılabilir istemci kimlik bilgisi türlerini ya da kullanırken listeler `BasicHttpBinding` veya `WSHttpBinding` Aktarım güvenlik modunda.  
  
|Tür|Açıklama|  
|----------|-----------------|  
|Yok.|İstemci kimlik sunmak gerekmez belirtir. Anonim istemci için çevirir.|  
|Temel|Temel kimlik doğrulaması. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]RFC 2617 – HTTP kimlik doğrulaması: Temel ve Özet kimlik doğrulaması, adresinde [http://go.microsoft.com/fwlink/?LinkId=84023](http://go.microsoft.com/fwlink/?LinkId=84023).|  
|Özet|Özet kimlik doğrulaması. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]RFC 2617 – HTTP kimlik doğrulaması: Temel ve Özet kimlik doğrulaması, adresinde [http://go.microsoft.com/fwlink/?LinkId=84023](http://go.microsoft.com/fwlink/?LinkId=84023).|  
|NTLM|NT LAN Yöneticisi (NTLM) kimlik doğrulaması.|  
|Windows|Windows kimlik doğrulaması.|  
|Sertifika|Kimlik doğrulaması, bir sertifika kullanılarak gerçekleştirilir.|  
|IssuedToken|Hizmetinin gerektiren izin verir, istemci kimlik doğrulaması ile veya bir güvenlik belirteci hizmeti tarafından verilmiş bir belirteç kullanarak [!INCLUDE[infocard](../../../../includes/infocard-md.md)]. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Federasyon ve verilen belirteçleri](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).|  
  
### <a name="message-client-credentials-in-bindings"></a>Bağlamaları ileti istemci kimlik bilgileri  
 Aşağıdaki tabloda, bir bağlama ileti güvenlik modunda kullanırken kullanılabilir istemci kimlik bilgisi türlerini listeler.  
  
|Tür|Açıklama|  
|----------|-----------------|  
|Yok.|Hizmetin anonim istemcilerle etkileşime girmesine izin verir.|  
|Windows|SOAP ileti alışverişlerinde Windows kimlik bilgisi kimliği doğrulanmış bağlamı altında yapılmasına izin verir.|  
|UserName|Hizmetinin gerektiren izin verir, istemci kimlik doğrulaması kullanıcı adı kimlik bilgilerini kullanarak. Güvenlik modu ayarlandığında unutmayın `TransportWithMessageCredential`, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] parola kullanarak ve böyle anahtarların ileti mod güvenliği için kullanarak Özet veya türetme anahtarları bir parola gönderme desteklemiyor. Bu nedenle, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] taşıma kullanıcı adı kimlik bilgileri kullanırken güvenli zorlar.|  
|Sertifika|Hizmetinin gerektiren izin verir, istemci kimlik doğrulaması kullanarak bir sertifika.|  
|IssuedToken|Özel belirteç sağlamak için bir güvenlik belirteci hizmeti kullanmak hizmet sağlar.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenlik genel bakış](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Hizmetler ve istemcileri güvenli hale getirme](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Bir kimlik bilgisi türü seçme](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [Özel bağlamalarla güvenlik özellikleri](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [Güvenlik davranışları](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Windows Server App Fabric için güvenlik modeli](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)