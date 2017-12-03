---
title: "Sertifika Kimlik Doğrulama ile Taşıma Güvenliği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
ms.assetid: 3d726b71-4d8b-4581-a3bb-02b9af51d11b
caps.latest.revision: "20"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: abff650bd7c0e613524e4903cc754b7ff4200328
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="transport-security-with-certificate-authentication"></a>Sertifika Kimlik Doğrulama ile Taşıma Güvenliği
Bu konu, taşıma güvenliği kullanırken X.509 sertifikalarını server ve istemci kimlik doğrulaması kullanarak açıklar. X.509 hakkında daha fazla bilgi için bkz: sertifikalar [X.509 ortak anahtar sertifikaları](http://msdn.microsoft.com/library/bb540819\(VS.85\).aspx). Sertifika bir üçüncü taraf veren sertifikalarının görülür bir sertifika yetkilisi tarafından verilmelidir. Bir Windows Server etki alanı Active Directory Sertifika Hizmetleri, istemci bilgisayarlar etki alanı için sertifikalar vermek üzere kullanılabilir. Daha fazla bilgi için bkz: [Windows 2008 R2 Sertifika Hizmetleri](http://go.microsoft.com/fwlink/?LinkID=209949&clcid=0x409). Bu senaryoda, hizmetin altında Internet Information Services (Güvenli Yuva Katmanı (SSL) ile yapılandırılmış olan IIS) barındırılıyor. Hizmet, istemcilerin sunucunun kimliğini doğrulamak bir SSL (X.509) sertifikası ile yapılandırılır. İstemci aynı zamanda istemci kimliğini doğrulamak hizmet veren bir X.509 sertifikası ile yapılandırılır. İstemci tarafından sunucunun sertifikası güvenilir olması gerekir ve istemcinin sertifika sunucusu tarafından güvenilir olması gerekir. Gerçek mekanizması nasıl hizmeti istemci doğrular ve birbirlerinin kimliğini, bu konu kapsamında değildir. Daha fazla bilgi için bkz: [wikipedia'da dijital imza](http://go.microsoft.com/fwlink/?LinkId=253157).  
  
 Bu senaryo tarafından Aşağıdaki diyagramda gösterildiği gibi bir istek/yanıt ileti deseni uygular.  
  
 ![Güvenli aktarım sertifikaları kullanarak](../../../../docs/framework/wcf/feature-details/media/8f7b8968-899f-4538-a9e8-0eaa872a291c.gif "8f7b8968-899f-4538-a9e8-0eaa872a291c")  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]bir sertifika bir hizmetle kullanma [sertifikalarla çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) ve [nasıl yapılır: bir SSL sertifikası ile bir bağlantı noktası yapılandırın](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md). Aşağıdaki tabloda senaryosu çeşitli özelliklerini açıklar.  
  
|Özelliği|Açıklama|  
|--------------------|-----------------|  
|Güvenlik modu|Taşıma|  
|Birlikte Çalışabilirlik|Mevcut Web hizmeti istemcileri ve Hizmetleri ile.|  
|Kimlik doğrulaması (sunucu)<br /><br /> Kimlik doğrulaması (istemci)|Evet (bir SSL sertifikası kullanarak)<br /><br /> Evet (bir X.509 sertifikası kullanarak)|  
|Veri bütünlüğü|Evet|  
|Veri gizliliği|Evet|  
|Taşıma|HTTPS|  
|Bağlama|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="configure-the-service"></a>Hizmetini yapılandırma  
 Bu senaryoda hizmeti IIS altında barındırılan olduğundan, bir web.config dosyası ile yapılandırılır. Aşağıdaki web.config nasıl yapılandırılacağını göstermektedir <xref:System.ServiceModel.WSHttpBinding> taşıma güvenliği ve X.509 istemci kimlik bilgilerini kullanmak için.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <protocolMapping>  
      <add scheme="https" binding="wsHttpBinding" />  
    </protocolMapping>  
    <bindings>  
      <wsHttpBinding>  
        <!-- configure wsHttp binding with Transport security mode and clientCredentialType as Certificate -->  
        <binding>  
          <security mode="Transport">  
            <transport clientCredentialType="Certificate"/>              
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>            
           <serviceDebug includeExceptionDetailInFaults="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="configure-the-client"></a>İstemciyi yapılandırma  
 İstemci kodu veya bir app.config dosyasında yapılandırılabilir. Aşağıdaki örnek kodda istemciyi Yapılandırma gösterilmektedir.  
  
```vb  
// Create the binding.  
WSHttpBinding myBinding = new WSHttpBinding();  
myBinding.Security.Mode = SecurityMode.Transport;  
myBinding.Security.Transport.ClientCredentialType =  
   HttpClientCredentialType.Certificate;  
  
// Create the endpoint address. Note that the machine name   
// must match the subject or DNS field of the X.509 certificate  
// used to authenticate the service.   
EndpointAddress ea = new  
   EndpointAddress("https://localhost/CalculatorService/service.svc");  
  
// Create the client. The code for the calculator   
// client is not shown here. See the sample applications  
// for examples of the calculator code.  
CalculatorClient cc =  
   new CalculatorClient(myBinding, ea);  
  
// The client must specify a certificate trusted by the server.  
cc.ClientCredentials.ClientCertificate.SetCertificate(  
    StoreLocation.CurrentUser,  
    StoreName.My,  
    X509FindType.FindBySubjectName,  
    "contoso.com");  
  
// Begin using the client.  
Console.WriteLine(cc.Add(100, 1111));  
//...  
cc.Close();  
```  
  
 Alternatif olarak aşağıdaki örnekte gösterildiği gibi bir App.config dosyasında istemci yapılandırabilirsiniz:  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <!-- this endpoint has an https: address -->  
      <endpoint address=" https://localhost/CalculatorService/service.svc "   
                behaviorConfiguration="endpointCredentialBehavior"  
                binding="wsHttpBinding"   
                bindingConfiguration="Binding1"   
                contract="Microsoft.Samples.TransportSecurity.ICalculator"/>  
    </client>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="endpointCredentialBehavior">  
          <clientCredentials>  
            <clientCertificate findValue="contoso.com"  
                               storeLocation="CurrentUser"  
                               storeName="My"  
                               x509FindType="FindBySubjectName" />  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <bindings>  
      <wsHttpBinding>  
        <!-- configure wsHttpbinding with Transport security mode  
                   and clientCredentialType as Certificate -->  
        <binding name="Binding1">  
          <security mode="Transport">  
            <transport clientCredentialType="Certificate"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
  </system.serviceModel>  
  
<startup><supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.0"/></startup></configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenlik genel bakış](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Windows Server App Fabric için güvenlik modeli](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)