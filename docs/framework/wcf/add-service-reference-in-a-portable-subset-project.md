---
title: "Taşınabilir Alt Küme Projesine Hizmet Başvurusu Ekle"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 61ccfe0f-a34b-40ca-8f5e-725fa1b8095e
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d7bd456b8c89c315321ad23683708d9dacc1dda2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="add-service-reference-in-a-portable-subset-project"></a>Taşınabilir Alt Küme Projesine Hizmet Başvurusu Ekle
Taşınabilir alt projeleri .NET derleme programcıların tek kaynak ağaç korumak ve birden çok .NET uygulamalarında (Masaüstü, Silverlight, Windows Phone ve XBOX) hala desteklerken oluşturma sistemi etkinleştirin. Taşınabilir alt projeleri üzerinde herhangi bir .NET uygulaması kullanılabilir bir .NET framework derlemesi olan .NET taşınabilir kitaplıklara yalnızca başvuru.  
  
## <a name="add-service-reference-details"></a>Hizmet başvurusu ayrıntılarını Ekle  
 Bir taşınabilir alt küme projesine hizmet başvurusu eklerken aşağıdaki sınırlamalar uygulanır:  
  
1.  İçin <xref:System.Xml.Serialization.XmlSerializer>, yalnızca sabit Kodlamalar izin verilir. SOAP Kodlamalar içeri aktarma sırasında bir hata oluşturur.  
  
2.  Kullanan Hizmetleri için <xref:System.Runtime.Serialization.DataContractSerializer> senaryolar, bir veri sözleşmesi yedek yeniden kullanılan türleri yalnızca taşınabilir alt geldiğini emin olmak için sağlanır.  
  
3.  Taşınabilir kitaplıklara desteklenmeyen bağlamaları Bel uç noktaları (dışındaki tüm bağlamaları <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSHttpBinding> işlem akışı, güvenilir oturumlar veya MTOM kodlama ve eşdeğer özel bağlama olmadan) göz ardı edilir.  
  
4.  İleti üstbilgilerini içe aktarma işleminden önce tüm işlemleri tüm ileti açıklamasında silinir.  
  
5.  Taşınamaz öznitelikleri <xref:System.ComponentModel.DesignerCategoryAttribute>, <xref:System.SerializableAttribute>, ve <xref:System.ServiceModel.TransactionFlowAttribute> oluşturulan istemci proxy kodundan kaldırılır.  
  
6.  ProtectionLevel SessionMode, IsInitiating, IsTerminating kaldırılma taşınamaz özellikleri <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.OperationContractAttribute>, ve <xref:System.ServiceModel.FaultContractAttribute>.  
  
7.  Tüm hizmet işlemlerini zaman uyumsuz işlemleri istemci proxy olarak üretilir.  
  
8.  Taşınabilir olmayan türler kullanan oluşturulan istemci oluşturucular kaldırılır.  
  
9. A <xref:System.Net.CookieContainer> örneği üzerinde oluşturulan istemci gösterilir.  
  
10. Açıklama, derleme ve sürüm kod oluşturucunun tanımlama dosyasının en üstte eklenir:`// This code was auto-generated by Microsoft.VisualStudio.Portable.AddServiceReference, version 1.0.0.0`  
  
11. <xref:System.Runtime.Serialization.ISerializable> Arabirimi desteklenmemektedir.  
  
12. Net.Tcp ve PollingDuplex bağlamaları desteklenmez.  
  
13. <xref:System.Runtime.Serialization.DataContractSerializer> Hataları için her zaman kullanılır.  
  
14. <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A>Taşınabilir alt projelerinde desteklenmiyor.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bir WCF istemcisi kullanarak hizmetlere erişme](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md)  
 [Taşınabilir sınıf kitaplığı](http://msdn.microsoft.com/library/gg597391\(v=vs.110\))