---
title: Derleme Bağlama Yönlendirmesi Güvenlik İzni
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 24a5cdff-7ed9-4195-93f3-edf6899019fc
author: mcleblanc
ms.author: markl
ms.openlocfilehash: e6690a4f11bb1a88e2d77c67ccb29056c8e03f96
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47088670"
---
# <a name="assembly-binding-redirection-security-permission"></a>Derleme Bağlama Yönlendirmesi Güvenlik İzni
Bir uygulama yapılandırma dosyasında açık derleme bağlama yeniden yönlendirmesi için bir güvenlik izni gerekir. Bu, .NET Framework derlemelerinin ve üçüncü tarafların derlemelerinin yeniden yönlendirilmesi için geçerlidir. İzin ayarlanarak verilir <xref:System.Security.Permissions.SecurityPermissionFlag> üzerinde bayrak <xref:System.Security.Permissions.SecurityPermission>. Yönetilen derlemeler varsayılan olarak izniniz yok.  
  
 Güvenilen Bölge (yerel makine) ve Intranet bölgesinde çalışan uygulamalar için güvenlik izni verilir. Internet bölgesinde çalışan uygulamalar, kesinlikle derleme bağlama yeniden yönlendirmesi gerçekleştirmesini yüklenmeleri yasaktır.  
  
 Derleme yeniden yönlendirme bileşenin yayımcı tarafından denetlenen bir yayımcı ilkesi dosyası ya da yönetici tarafından denetlenen makine yapılandırma dosyası gerçekleştirilirse izin gerekli değildir. Ancak, yayımcı ilkesi kullanarak açıkça yoksaymak bir uygulama için izin gerekiyor [ \<publisherPolicy uygulama = "Hayır" / >](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) uygulama yapılandırma dosyasında öğesi.  
  
 Aşağıdaki tabloda, varsayılan güvenlik ayarlarını gösterir. **SecurityPermission** bayrağı.  
  
|Bölge|SecurityPermission bayrağını ayarlama|  
|----------|-----------------------------------|  
|Güvenilir bölgeye (yerel makine)|**AÇIK**|  
|Intranet bölgesi|**AÇIK**|  
|Internet Bölgesi|**KAPALI**|  
|Güvenilmeyen bölgeleri|**KAPALI**|  
  
 Bir yönetici veya kısıtlama belirli bir bilgisayardaki belirli senaryoları desteklemek üzere bu güvenlik ayarlarını değiştirebilirsiniz. Değiştirmek için araçları yoktur **SecurityPermission** ; varsayılan ayarı bayrağı yönetici el ile bir kullanıcının bilgisayarında Security.config dosyayı düzenlemeniz gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yayımcı ilkesi dosyaları ve yan yana yürütme](https://msdn.microsoft.com/library/97a042be-4d72-40c3-91c0-76fd36bdf133)  
 [Nasıl yapılır: Otomatik Bağlama Yönlendirmesini Etkinleştirme veya Devre Dışı Bırakma](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)  
 [Yan Yana Yürütme](../../../docs/framework/deployment/side-by-side-execution.md)
