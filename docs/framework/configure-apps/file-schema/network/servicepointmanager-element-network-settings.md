---
title: '&lt;servicePointManager&gt; öğesi (ağ ayarları)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#servicePointManager
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/servicePointManager
helpviewer_keywords:
- servicePointManager element
- <servicePointManager> element
ms.assetid: 6e5def51-3646-4ef6-a7bd-c69151321bec
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 2aaf590975d9fd3f5d78cb64d8d2b1c38c0e8dc7
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47202542"
---
# <a name="ltservicepointmanagergt-element-network-settings"></a>&lt;servicePointManager&gt; öğesi (ağ ayarları)
Ağ kaynaklarına bağlantılarını yapılandırır.  
  
 \<Yapılandırma >  
\<system.net>  
\<Ayarlar >  
\<servicePointManager >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<servicePointManager  
  checkCertificateName="true|false"  
  checkCertificateRevocationList="true|false"  
  encryptionPolicy="AllowNoEncryption|NoEncryption|RequireEncryption"  
  expect100Continue="true|false"  
  useNagleAlgorithm="true|false"  
  enableDnsRoundRobin="true|false"  
  dnsRefreshTimeout="time"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|**Öznitelik**|**Açıklama**|  
|-------------------|---------------------|  
|`checkCertificateName`|Sistem sertifika kullanmadan önce sertifikasındaki ad sunucusu konak adı eşleştiğini doğrulayın olup olmadığını belirtir. Varsayılan değer `true` şeklindedir.|  
|`checkCertificateRevocationList`|Sistem sertifika kullanmadan önce sertifika iptal olup olmadığını denetleyip denetlemeyeceğini belirtir. Varsayılan değer `false` şeklindedir.|  
|`dnsRefreshTimeout`|Milisaniye cinsinden DNS hepsini bir kez deneme seçeneği ile birlikte ne kadar etki alanı adı hizmeti (çözümleri önbelleğe alınan DNS) belirtir. Varsayılan değer 120.000 (iki dakika) milisaniyedir.|  
|`enableDnsRoundRobin`|Ana bilgisayarın DNS çözümleri adları olup olmadığını birden çok Internet Protokolü (IP) adresi ile dönüş tüm adresleri ya da yalnızca ilk eşleşmenin belirtir. Varsayılan değer `false` şeklindedir.|  
|`encryptionPolicy`|Bir SSL/TLS oturumuna uygulanan şifreleme ilkesi belirtir bir <xref:System.Net.ServicePointManager> örneği. Olası değerler şunlardır: değerlerini eşdeğer <xref:System.Net.Security.EncryptionPolicy> sabit listesi. Kullanımını <xref:System.Security.Authentication.CipherAlgorithmType.Null> şifreleme ilkesi ayarlandığında gereklidir `NoEncryption`. Varsayılan değer `RequireEncryption` şeklindedir.|  
|`expect100Continue`|POST yöntemleri almayı beklemelisiniz olup olmadığını belirten bir `100-continue` sunucu yanıtı. Varsayılan değer `true` şeklindedir.|  
|`useNagleAlgorithm`|Hizmet Noktası Yöneticisi tarafından denetlenen bağlantıları Nagle algoritma kullanıp kullanmadığını belirtir. Varsayılan değer `true` şeklindedir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Öğe**|**Açıklama**|  
|-----------------|---------------------|  
|[Ayarlar](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|Temel ağ seçeneklerini yapılandırır <xref:System.Net> ad alanı.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="configuration-files"></a>Yapılandırma Dosyaları  
 Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Net.ServicePointManager>  
 <xref:System.Net.Security.EncryptionPolicy>  
 [Ağ Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
