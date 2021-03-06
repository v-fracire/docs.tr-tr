---
title: Kuyruğa Alınan Bir Uygulamayı Web'de Barındırma
ms.date: 03/30/2017
ms.assetid: c7a539fa-e442-4c08-a7f1-17b7f5a03e88
ms.openlocfilehash: f396ffadeca81d86d867842b63cad3c63d67ff3a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="web-hosting-a-queued-application"></a>Kuyruğa Alınan Bir Uygulamayı Web'de Barındırma
Windows İşlem Etkinleştirme Hizmeti (WAS) etkinleştirme ve uygulamaları Windows Communication Foundation (WCF) hizmetlerini barındırmak içeren çalışan işlemleri ömrü yönetir. WAS işlem modelini genelleştirir [!INCLUDE[iis601](../../../../includes/iis601-md.md)] işlem modeli HTTP bağımlılığını kaldırarak HTTP sunucusu. Bu, hem HTTP hem de net.msmq ve ileti tabanlı etkinleştirme destekler ve verilen bir bilgisayardaki uygulamaları, çok sayıda konak olanağı sunar bir barındırma ortamında msmq.formatname gibi HTTP olmayan protokolleri kullanmak WCF hizmetleri sağlar.  
  
 OLAN bir veya daha fazla iletiler bir uygulama tarafından kullanılan sıraların yerleştirilir kuyruğa alınan bir uygulamayı etkinleştirir bir Message Queuing (MSMQ) etkinleştirme hizmeti içerir. MSMQ Etkinleştirme hizmeti varsayılan olarak otomatik olarak başlatılan bir NT hizmetidir.  
  
 WAS ve onun avantajlarını hakkında daha fazla bilgi için bkz: [Windows İşlem Etkinleştirme hizmetinde barındırma](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md). MSMQ hakkında daha fazla bilgi için bkz: [kuyruklar genel bakış](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
  
## <a name="queue-addressing-in-was"></a>WAS içinde adresleme sırası  
 Uygulamaları Tekdüzen Kaynak Tanımlayıcısı (URI) adreslerine sahip oldu. Uygulama adreslerine sahip iki bölümden oluşur: temel bir URI öneki ve uygulamaya özgü, göreli adresi (yol). Bu iki bölümden birlikte katıldığında bir uygulama için dış adresini sağlayın. Taban URI öneki site bağlamayı oluşturulur ve örneğin, "net.msmq://localhost", "msmq.formatname://localhost" veya "net.tcp://localhost" site altındaki tüm uygulamalar için kullanılır. Uygulama adresleri ardından oluşturulur uygulamaya özgü yol parçaları gerçekleştirerek (gibi "/ applicationOne") ve taban URI ekleme önek tam uygulamayı URI, örneğin, gelmesi "net.msmq://localhost/applicationOne".  
  
 MSMQ Etkinleştirme hizmeti, MSMQ Etkinleştirme hizmeti, iletileri izlemelisiniz sıranın eşleştirmek için uygulama URI'sini kullanır. MSMQ Etkinleştirme hizmeti başladığında, almak üzere yapılandırıldığında ve iletileri izler, bilgisayardaki tüm ortak ve özel sıralarda numaralandırır. Her 10 dakikada MSMQ Etkinleştirme hizmeti izlemek için kuyrukları listesini yeniler. Bir kuyruktaki bir ileti bulunduğunda, Etkinleştirme hizmeti en uzun eşleşen uygulamaya URI net.msmq bağlama için kuyruk adı ile eşleşen ve uygulama etkinleştirir.  
  
> [!NOTE]
>  Etkinleştirilmekte olan uygulama (en uzun eşleşme) sıra adı öneki ile eşleşmesi gerekir.  
  
 Örneğin, bir sıra adıdır: msmqWebHost/orderProcessing/service.svc. Bir sanal dizin /msmqWebHost/orderProcessing service.svc altındaki ile uygulama 1 varsa ve uygulama 2'in altındaki bir orderProcessing.svc ile bir sanal dizin /msmqWebHost vardır, uygulama 1 etkinleştirilir. Uygulama 1 silinirse, uygulama 2 etkinleştirilir.  
  
> [!NOTE]
>  Bir sıra oluşturulduğunda MSMQ Etkinleştirme hizmeti, en fazla 10 Sıranın oluşturulduğu zamandan dakikadır sırası listesi yeniler kadar kendisine gönderilen iletileri bir uygulama etkinleştirmeyin. Etkinleştirme hizmetini yeniden başlatma yanı sıra listesini yeniler.  
  
### <a name="the-effect-of-private-and-public-queues-on-addressing"></a>Adresleme üzerinde etkisi özel ve genel sıraların  
 MSMQ Etkinleştirme hizmeti, özel ve genel sıra izleme arasında ayrım yapmaz. Bu nedenle, ortak ve özel sıralar aynı ada sahip olamaz. Bunu yaparsanız, Web barındırdığı bir uygulama sıraları birinden okuma devreye.  
  
### <a name="queue-configuration-for-activation"></a>Etkinleştirme için sıra yapılandırması  
 MSMQ Etkinleştirme hizmeti, ağ hizmeti olarak çalışır. Uygulamaları etkinleştirmek için kuyrukları izler hizmetidir. Sıra, sıranın uygulamalardan etkinleştirmek, erişim denetim listesi (ACL) iletiler için gözatmak ağ hizmeti erişim sağlamanız gerekir.  
  
### <a name="poison-messaging"></a>Zehirli ileti  
 Zehirli ileti işleme WCF'de yalnızca bir ileti zarar ancak kullanıcı yapılandırmasını temel alarak bir değerlendirme seçer algılar kanal tarafından işlenir. Sonuç olarak, sırada tek bir ileti yoktur. Web barındırılan uygulama ardışık kez durdurur ve yeniden deneme kuyruğuna ileti taşınır. Yeniden deneme döngüsü gecikmesini tarafından dikte bir noktada, ileti yeniden deneme sıradan ana sıranın yeniden denemek için taşınır. Ancak bu sıraya alınan kanal etkin olmasını gerektirir. Uygulama tarafından WAS Geri Dönüşüm, başka bir ileti kuyruğa alınan uygulamayı etkinleştirmek için ana sıraya gelene kadar ileti yeniden deneme sırada kalır. Çözüm ileti el ile yeniden deneme sıradan geri uygulamayı yeniden etkinleştirmek için ana kuyruğa taşımak için bu durumda olabilir.  
  
### <a name="subqueue-and-system-queue-caveat"></a>Alt sırasına ve sistem sırası uyarısıyla  
 WAS barındırdığı bir uygulama, sistem genelinde atılacak veya zararlı Alt sıralar gibi alt sıralar gibi bir sistem sıradaki iletiler göre etkinleştirilemiyor. Bu ürünün bu sürümü için bir kısıtlamadır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Zehirli İleti İşleme](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)  
 [Hizmet Uç Noktaları ve Kuyruk İşleme](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md)
