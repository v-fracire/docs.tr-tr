---
title: Windows Store uygulamaları için ağ yalıtımı
ms.date: 03/30/2017
ms.assetid: b064497c-d956-46b8-838d-7a0223c7e200
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 97096d6fa41cd25a92c23cd47008b33fb6037190
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47195413"
---
# <a name="network-isolation-for-windows-store-apps"></a>Windows Store uygulamaları için ağ yalıtımı
Sınıflar <xref:System.Net>, <xref:System.Net.Http>, ve <xref:System.Net.Http.Headers> ad alanlarında, Windows Store uygulamaları veya Masaüstü uygulamaları geliştirmek için kullanılabilir. Bir Windows Store uygulaması kullanıldığında, bu ad alanlarında sınıflar tarafından kullanılan uygulama güvenlik modelinin bir parçası olan ağ yalıtımı etkilenir [!INCLUDE[win8](../../../includes/win8-md.md)]. Uygun ağ yeteneklerini, sistemin ağ erişimine izin ver Windows Store uygulaması için uygulama bildirimindeki etkinleştirilmelidir.  
  
## <a name="checklist-for-network-isolation"></a>Ağ yalıtımı için Denetim listesi  
 Ağ yalıtımı, Windows Store uygulaması için yapılandırıldığından emin olmak için bu denetim listesini kullanın.  
  
1.  Ağ erişimi isteklerini uygulama tarafından gereken yönü belirler. Bu istemci tarafından başlatılan giden istekleri ya da istenmeyen gelen istekleri olabilir veya bu ağ istek türleri her ikisinin bir birleşimi olabilir.  
  
2.  Bu uygulama ile iletişim kurar ve ağ kaynaklarını türünü belirler. Bir uygulama bir ev veya iş ağı üzerinde güvenilen kaynaklarla iletişim gerekebilir. Bir uygulamayı Internet'teki kaynaklarla iletişim gerekebilir. Uygulama, her iki türdeki ağ kaynaklarına erişimi gerekebilir.  
  
3.  Ağ yalıtımı gereken en düşük özellikleri uygulama bildirimine yapılandırın.  
  
4.  Dağıtın ve sorun giderme için sağlanan ağ yalıtımı araçları kullanarak test etmek için uygulamanızı çalıştırın.  
  
 Ağ özellikleri ve ağ yalıtımı sorun giderme için kullanılan yalıtım araçları yapılandırma hakkında daha ayrıntılı bilgi için bkz. [ağ yalıtımı özelliklerini yapılandırma](https://go.microsoft.com/fwlink/?LinkID=228265) içinde [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] Geliştirici belgeleri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bir web hizmetine bağlanma](https://go.microsoft.com/fwlink/?LinkID=245696)  
 [Yönergeler ve ağ yalıtımı için Denetim listesi](https://go.microsoft.com/fwlink/?LinkID=228265)  
 [Hızlı Başlangıç: HttpClient'ı kullanarak bağlanma](https://go.microsoft.com/fwlink/?LinkId=245697)  
 [HttpClient işleyicilerini kullanma](https://go.microsoft.com/fwlink/?LinkId=245699)  
 [HttpClient bağlantıları güvenliğini sağlama](https://go.microsoft.com/fwlink/?LinkId=245698)  
 [HttpClient örneği](https://go.microsoft.com/fwlink/?LinkId=242550)
