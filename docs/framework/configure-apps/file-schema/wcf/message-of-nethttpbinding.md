---
title: '&lt;netHttpBinding&gt; &lt;iletisi&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9def5a35-475d-40d6-b716-ccdbd93863c7
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9ee45fe84a7134eea442b19a6f3e123a464cbb5a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltmessagegt-of-ltnethttpbindinggt"></a>&lt;netHttpBinding&gt; &lt;iletisi&gt;
İleti düzeyi güvenliği ayarlarını tanımlar [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).  
  
 \<Sistem. ServiceModel >  
\<bağlamaları >  
\<netHttpBinding >  
\<bağlama >  
\<Güvenlik >  
\<İleti >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<message   
   algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="UserName/Certificate"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|algorithmSuite|İleti şifreleme ve anahtar-wrap algoritmaları ayarlar. Bu öznitelik türünde <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, algoritmalar ve anahtar boyutları belirtir. Bu algoritmalar, güvenlik ilkesi dili (WS-SecurityPolicy) belirtiminde belirtilen eşlenir.<br /><br /> Varsayılan değer `Basic256` şeklindedir.|  
|clientCredentialType|İleti tabanlı güvenlik kullanarak istemci kimlik doğrulaması yapılırken kullanılacak kimlik bilgileri türünü belirtir. Varsayılan, `UserName` değeridir.|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|UserName|-İstemci kimlik doğrulaması bir kullanıcı adı kimlik bilgisi sunucuda gerektirir. Bu kimlik bilgilerini kullanarak belirtilmesi gerekiyor <`clientCredentials`> öğesi.<br />-   [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]bir parola Özet gönderme veya parolaları kullanmanızı ve ileti güvenliği için bu anahtarları kullanarak anahtarları türetme desteklemez. Bu nedenle, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] taşıma kullanıcı adı kimlik bilgileri kullanılırken korunması gerektiğini zorlar. İçin `basicHttpBinding`, bu SSL kanalı oluşturulması gerekir.|  
|Sertifika|Bir sertifika kullanarak sunucuya istemcinin kimliğinin doğrulanmasını gerektirir. İstemci kimlik bilgileri bu durumda kullanarak belirtilmesi gerekiyor <`clientCredentials`> ve <`clientCertificate`>. Ayrıca, ileti güvenlik modunu kullanırken, istemci ile hizmet sertifikası hazırlanması gerekir. Hizmet kimlik bilgilerini bu durumda kullanarak belirtilmesi gerekiyor <xref:System.ServiceModel.Description.ClientCredentials> sınıfı veya `ClientCredentials` davranışı öğesi ve hizmet belirterek sertifika kullanarak \<serviceCertificate > öğesi ServiceCredentials.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|<`security`> öğesi <`netHttpBinding`>|Güvenlik özellikleri için tanımlar <`netHttpBinding`> öğesi.|  
  
## <a name="example"></a>Örnek  
 Bu örnek, basicHttpBinding ve ileti güvenliği kullanan bir uygulamayı uygulamak gösterilmiştir. Aşağıdaki yapılandırma örneği bir hizmet için uç nokta tanımı basicHttpBinding belirtir ve adlı bir bağlama yapılandırması başvuran `Binding1`. Hizmetin kendisi için istemci kimlik doğrulaması için kullandığı sertifika kümesinde `behaviors` altında yapılandırma dosyasının `serviceCredentials` öğesi. İstemci hizmete kendi kimliğini doğrulamak için kullandığı sertifikayı uygulandığı doğrulama modu da kümesinde `behaviors` altında bölümünde `clientCertificate` öğesi.  
  
 Aynı bağlama ve güvenlik ayrıntıları istemci yapılandırma dosyasında belirtilir.  
  
```xml  
<system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
          </baseAddresses>  
        </host>  
        <!-- this endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service  -->  
        <endpoint address=""  
                  binding="basicHttpBinding"  
                  bindingConfiguration="Binding1"   
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
  
    <bindings>  
      <basicHttpBinding>  
        <!--   
        This configuration defines the SecurityMode as Message and   
        the clientCredentialType as Certificate.  
        -->  
        <binding name="Binding1" >  
          <security mode = "Message">  
            <message clientCredentialType="Certificate"/>  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <!--  
        The serviceCredentials behavior allows one to define a service certificate.  
        A service certificate is used by a client to authenticate the service and provide message protection.  
        This configuration references the "localhost" certificate installed during the setup instructions.  
        -->  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
            <clientCertificate>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it will be trusted without performing a  
            validation of the certificate's issuer chain. This setting is used here for convenience so that the   
            sample can be run without having to have certificates issued by a certification authority (CA).  
            This setting is less secure than the default, ChainTrust. The security implications of this   
            setting should be carefully considered before using PeerOrChainTrust in production code.   
            -->  
              <authentication certificateValidationMode="PeerOrChainTrust" />  
            </clientCertificate>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hizmetler ve istemcileri güvenli hale getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Bağlamaları](../../../../../docs/framework/wcf/bindings.md)  
 [Sistem tarafından sağlanan bağlamaları yapılandırma](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<bağlama >](../../../../../docs/framework/misc/binding.md)