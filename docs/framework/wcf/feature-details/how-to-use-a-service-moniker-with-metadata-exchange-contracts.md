---
title: "Nasıl yapılır: Meta Veri Değişimi Sözleşmeleriyle Hizmet Bilinen Adı Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c41a07e5-cb9d-45d6-9ea4-34511e227faf
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ed6ce9b87a5e2d8945a57110c02cce8024439f14
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-a-service-moniker-with-metadata-exchange-contracts"></a>Nasıl yapılır: Meta Veri Değişimi Sözleşmeleriyle Hizmet Bilinen Adı Kullanma
Bazı yeni geliştirme sonra [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmetleri karar bir komut dosyası veya Visual Basic 6.0 uygulamadan bu hizmetleri çağıran kullanabilmek ister. Bir yöntem oluşturmak için olacak bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci derleme derlemesini COM ile kaydetme, derlemeyi GAC'ye yükleyin ve ardından Visual Basic kodunuzdan COM türlerini başvuru. Uygulamayı dağıttığınızda, dağıtmanız gerekecek [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci derleme. Ardından, kullanıcı WCF istemcisi derlemesini COM ile kaydetme ve GAC'ye yerleştirmek sahip olur. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]COM birlikte çalışma de aynı hizmet çağrıları öğesine bağlı kalmadan almanıza imkan tanır bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci derleme. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Ad herhangi bir çağrıda olanak tanır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet herhangi bir dilden bir meta veri exchange (Mex) uç noktası kullanan hizmet adının URI belirterek COM uyumlu (Visual Basic, VBScript, Visual Basic for Applications (VBA) ve benzeri) hizmeti hakkında türü bilgi ayıklamak için. Bu konu, Başlarken çağrılacağını açıklar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kullanarak örnek bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Mex uç nokta belirtir ad.  
  
> [!NOTE]
>  Tanımlanan türlerden [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci derleme aslında hiç örneği. Derleme yalnızca meta veriler için kullanılır.  
  
### <a name="using-the-service-moniker-with-a-mex-address"></a>Mex adresi ile hizmet bilinen adı kullanma  
  
1.  Başlarken örneği oluşturmak ve hizmetin çalıştığından emin olmak için URL'ye (http://localhost/ServiceModelSamples/Service.svc) göz atmak için Internet Explorer'ı kullanın.  
  
2.  Visual Basic komut dosyası veya aşağıdaki kodu içeren bir Visual Basic uygulama oluşturun:  
  
    ```  
    monString = "service:mexaddress=http://localhost/ServiceModelSamples/Service.svc/MEX"  
    monString = monString + ", address=http://localhost/ServiceModelSamples/Service.svc"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set calc = GetObject(monString)  
    MsgBox calc.Add(3, 4)  
    ```  
  
3.  Visual Basic uygulama veya komut dosyasını çalıştırın.  
  
    > [!NOTE]
    >  Aradığınız hizmeti Mex bitiş noktası ad hizmeti meta verileri okuyabilir için kullanıma gerekir. Daha fazla bilgi için bkz: [nasıl yapılır: bir yapılandırma dosyası kullanarak bir hizmet için meta veri yayımlama](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).  
  
    > [!NOTE]
    >  Ad hatalı veya hizmet kullanılamıyor çağrısı `GetObject` "Geçersiz sözdizimi." bildiren bir hata döndürür  Bu hatayı alırsanız, kullanmakta olduğunuz adının doğru olduğundan ve hizmet kullanılabilir olduğundan emin olun.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Windows Communication Foundation Hizmeti bilinen adını kaydolmadan kullanma](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)  
 [Nasıl yapılır: WSDL sözleşmeleriyle hizmet bilinen adı kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)